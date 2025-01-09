# Identity Verification System

## 1. Overview
The identity verification system consists of registrars who verify specific fields of user identities. The system uses bitflags to specify verification fields and proxies for secure operation.

## 2. Identity Fields and Bitflags

### Field Positions
Each identity field corresponds to a specific bit position in a binary number:
```
Position | Field         | Binary Value      | Decimal Value
---------|--------------|-------------------|---------------
9        | Discord      | 0b1000000000      | 512
8        | GitHub       | 0b0100000000      | 256
7        | Twitter      | 0b0010000000      | 128
6        | Image        | 0b0001000000      | 64
5        | PgpFingerprint| 0b0000100000     | 32
4        | Email        | 0b0000010000      | 16
3        | Matrix       | 0b0000001000      | 8
2        | Web          | 0b0000000100      | 4
1        | Legal        | 0b0000000010      | 2
0        | Display      | 0b0000000001      | 1
```

### Common Combinations
```
Standard Verification (665):
Discord + Twitter + Email + Matrix + Display
1010011001 = 512 + 128 + 16 + 8 + 1 = 665
```

## 3. Setting Up a Registrar

### Setting Fields
```rust
identity.setFields(registrarIndex, fields)
```
Example:
```
identity.setFields(0, 665)  // Sets registrar 0 to verify Display, Matrix, Email, Twitter, Discord
```

### Field Validation
- Chain automatically blocks judgment requests that don't match registrar's fields
- All specified fields must be present in identity information
- Extra fields are ignored for verification purposes

## 4. Proxy System

### Setting Up Proxy
```rust
proxy.addProxy(delegate, proxyType, delay)
```

Parameters:
- `delegate`: Hot wallet address for making judgments
- `proxyType`: IdentityJudgement
- `delay`: 0 (no delay for judgments)

### Proxy Types Available
```rust
pub enum ProxyType {
    Any,               // Full permissions
    NonTransfer,       // Non-financial calls
    CancelProxy,       // Cancel proxy announcements
    Identity,          // All identity calls
    IdentityJudgement, // Only judgment calls
    Collator          // Collator selection calls
}
```

## 5. Judgment Process

### Available Judgments
```rust
pub enum Judgement {
    Unknown,            // 0
    FeePaid(u128),     // 1 - Judgement Requested from registrar(index)
    Reasonable,        // 2 - Standard positive judgment
    KnownGood,         // 3
    OutOfDate,         // 4
    LowQuality,        // 5
    Erroneous         // 6 - Used for failed verifications
}
```

### Making Judgments via Proxy
```rust
proxy.proxy(
    registrarAccount,
    Some(IdentityJudgement),
    identity.provideJudgement(regIndex, target, judgement, identityHash)
)
```

## 6. Security Considerations

### Chain-Level Security
- Automatic field validation
- Proxy system limits exposure of registrar account
- Identity hash changes trigger new verification requirements

### Best Practices
1. Use cold storage for main registrar account
2. Set up proxy for daily operations
3. Regularly verify proxy permissions
4. Monitor identity hash changes

## 7. Implementation Example

### Standard Setup Process
1. Get registered as a registrar
2. Set verification fields:
   ```
   identity.setFields(registrarIndex, 665)
   ```
3. Set up proxy:
   ```
   proxy.addProxy(hotWalletAddress, IdentityJudgement, 0)
   ```
4. Use hot wallet for judgments:
   ```
   proxy.proxy(registrarAccount, Some(IdentityJudgement), 
              identity.provideJudgement(...))
   ```

### Field Verification
The system automatically ensures:
- All required fields are present
- Fields match registrar's bitflag specification
- Identity hash consistency
- Proper proxy permissions

## 8. Important Notes
- Identity hashes change when verified fields are modified
- Only specified fields are considered for verification
- Proxy permissions cannot be exceeded
- Chain enforces all validation rules
- Registrar must handle both successful (Reasonable) and failed (Erroneous) cases
