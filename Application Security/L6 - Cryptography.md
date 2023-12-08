### .NET Cryptography Model
- .NET provides implementations of many standard cryptographic algorithms.
- Algorithm Type classes
	- `SymmetricAlgorithm`
	- `AsymmetricAlogorithm`
	- `HashAlgorithm`
- Algorithm classes (Inherits from Type classes)
	- AES
	- RSA
	- ECDiffieHellman
- Implementation classes (Inherits from Algorithm classes)
	- `AesManaged`
	- `RC2CryptoServiceProvider`
	- `ECDiffieHellmanCng`

### Cryptography Library
- Under the `System.Security.Cryptography` namespace, we have:
	- `SymmetricAlgorithm`

### Salted/Unsalted hashes
^cefd82
**Salted Hash**
- Made up of random bits added to each password instance before its hashing.
- Creating a unique passwords even in the instance of two users choosing the same password.
- Helps mitigate hash table attacks.

**Unsalted Hash**
- Hashing using special mathematical function that performs one-way encryption without adding additional random bits to the password before its hashing.