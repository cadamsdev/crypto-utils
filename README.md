# RSA Utils
A simple library to easily encrypt and decrypt your data using the RSA algorithm.

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
