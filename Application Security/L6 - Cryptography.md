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
		- Encapsulate symmetric algorithms such as DES and Rijndeal(AES).
	- `AsymmetricAlgorithm`
		- Encapsulate the asymmetric algorithms such as RSA and DSA.
	- `HasAlgorithm`
		- Base call of all cryptographic hash algorithms.
	- `ToBase64Transform` and `FromBase64Transform`
		- Allows for conversion between byte stream and base64 representation.
	- `CryptographicException`
		- Error information for cryptographic operations.

### Symmetric Algorithms
- Encryption and decryption use the same secret key.
- Primary attack is "brute force" key search - (try every possible key)
- Key distribution and storage is difficult.
- Relatively fast.
- Advanced Encryption Standard (AES)
	- US government standard since 2001 (replaced DES)
	- Rijndeal algorithm (with 128 bit block size)
- From plaintext (unencrypted data), data can be encrypted using a shared secret key. A cyphertext is then sent to the receiving party, the receiving party uses the shared secret key to 

### Salted/Unsalted hashes
^cefd82
**Salted Hash**
- Made up of random bits added to each password instance before its hashing.
- Creating a unique passwords even in the instance of two users choosing the same password.
- Helps mitigate hash table attacks.

**Unsalted Hash**
- Hashing using special mathematical function that performs one-way encryption without adding additional random bits to the password before its hashing.