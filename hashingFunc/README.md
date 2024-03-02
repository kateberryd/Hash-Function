## Cryptographic SHA256 Hash function

This is a simple implementation of a cryptographic hash function in Javasacript 

This function recieves an input and return the hash of that input

This function uses WEB API CRYPTO to run

x`

```js=
async function hashFunc(value) {
    
    // We use the crypto.subtle.digest
    // method from the Web Crypto API to 
    // calculate the SHA-256 hash.
    // the TextEncoder().encode(input) converts 
    // the input string into a Uint8Array buffer.
    

        const buffer = await crypto.subtle.digest(
            "SHA-256",
            new TextEncoder().encode(value)
        );
    
    // The result of the digest is a buffer, and we 
    // convert it to a hexadecimal string. 
    // We use the spread operator (...) to convert 
    // the Uint8Array buffer to an array, and then 
    // map each byte to its hexadecimal representation. 
    // The padStart(2, '0') ensures that each byte 
    // is represented by two characters, and join('') 
    // concatenates them into a single string
    
        return [...new Uint8Array(buffer)]
            .map((b) => b.toString(16).padStart(2, "0"))
            .join("")
}

```


To use the function above 

``` js=

// Example usage:
const input = "Sample Text";
hashFunc(input).then((hashedData) =>
    console.log(`Input: ${input}\nSHA-256 Hash: ${hashedData}`)
);


```
You should expect something like this 


![Screenshot 2024-02-29 at 00.29.57](https://hackmd.io/_uploads/SkgDfH6nT.png)



