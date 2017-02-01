# Crypto Utils
A simple library for easily encrypting and decrypting data using either AES, RSA or combined algorithms.

# AESUtils
A simple library to easily encrypt and decrypt data using the AES algorithm.

## Features
* Use a random key
* Create a key from a password
* Can specify a salt with a password for better encryption
* Can decrypt data with a password
* Write key to file
* Retrieve a key from a file
* Super easy to use

## Examples
### Using a random key
```java

		// the bytes you want to encrypt
		byte[] message = "Hello world!".getBytes();

		// create a random key
		SecretKey secretKey = AESUtils.generateKey();
	
		// encrypt the message using the key that was generated
		byte[] encrypted = AESUtils.encrypt(secretKey, message);

		// decrypt the message by using the key again
		byte[] decrypted = AESUtils.decrypt(secretKey, encrypted);

		// results
		System.out.println("original: " + new String(message));
		System.out.println("encrypted: " + new String(encrypted));
		System.out.println("decrypted: " + new String(decrypted));
```

### Result

```
original: Hello world!
encrypted: ù2è–®ÃÑ¦DçÆÔ/šÙÆ
decrypted: Hello world!
```

### Using your own password as the key

```java

		// the bytes you want to encrypt
		byte[] message = "Hello world!".getBytes();

		// create a key by using your own password
		SecretKey secretKey = AESUtils.createKey("password");
	
		// encrypt the message using the key that was generated
		byte[] encrypted = AESUtils.encrypt(secretKey, message);

		// decrypt the message by entering a password
		byte[] decrypted = AESUtils.decrypt("password", encrypted);

		// results
		System.out.println("original: " + new String(message));
		System.out.println("encrypted: " + new String(encrypted));
		System.out.println("decrypted: " + new String(decrypted));
```

### Result

```
original: Hello world!
encrypted: O¥e†Å8Qúµd³Ç
decrypted: Hello world!
```


# RSAUtils
A simple library to easily encrypt and decrypt data using the RSA algorithm.

## Features
* Generates both random public and private keys
* 2048 size
* Get public key object from file
* Get private key object from file
* Super easy to use

# Example
```java

	public static void main(String[] args) throws Exception {
	
		byte[] data = "hello cryptography".getBytes();
		
		RSAUtils.generateKey("./public.key", "./private.key");		

		PublicKey publicKey = RSAUtils.getPublicKey("./public.key");

		byte[] encrypted = RSAUtils.encrypt(publicKey, data);		

		PrivateKey privateKey = RSAUtils.getPrivateKey("./private.key");

		byte[] decrypted = RSAUtils.decrypt(privateKey, encrypted);		

		System.out.println("original: " + new String(data));
		System.out.println("encrypted: " + new String(encrypted));
		System.out.println("decrypted: " + new String(decrypted));

	}
```
