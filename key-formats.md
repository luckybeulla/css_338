***Lucky Beulla Muhoza***

***CS 338***

***Prof. Jeff Ondich***

## SSH KEY FILE FORMATS ##
**----PRIVATE KEY----** 

The private key is expected to contain the following items as per [Appendix 1.2 of RFC 8017](https://datatracker.ietf.org/doc/html/rfc8017#appendix-A.1.2), the private key is expected to contain the following integers: 

<img width="781" alt="Screenshot 2024-10-02 at 11 36 10 AM" src="https://github.com/user-attachments/assets/8aa13e81-ab67-471e-89a1-7a3484a8e8cd">

After I generated my private key using the **ssh-keygen -t rsa -m pem** commandline, I copyied the contents of the file containing the private key to my clipboard (cat id_rsa_homework | pbcopy) and pasted them into the [Lapo Luchini ASN1 decoder](https://lapo.it/asn1js/). 

The decoded elements of my private key are: 

<img width="932" alt="Screenshot 2024-10-02 at 11 37 38 AM" src="https://github.com/user-attachments/assets/a27ff689-ff63-458c-8fd9-985a98f124aa">

**----PUBLIC KEY----**

Refering to the [Appendix 1.1 of RFC 8017](https://datatracker.ietf.org/doc/html/rfc8017#appendix-A.1.1), the elements of the RSA public key are expected to be: 

<img width="681" alt="Screenshot 2024-10-02 at 7 11 30 PM" src="https://github.com/user-attachments/assets/0f241211-8bf1-4802-b5b8-61aba5968d29">

By decoding the contents of my generated public key, I used the **ssh-keygen -f id_rsa_homework.pub -e -m pem > id_rsa_homework.pub.pem** commandline to convert the my public key from OpenSSH to the more generic PKCS#1 PEM file format. I then copy and pasted the contents of id_rsa_homework.pub.pem into the [Lapo Luchini ASN1 decoder](https://lapo.it/asn1js/). 

Here is my decoded public key: 

<img width="1009" alt="Screenshot 2024-10-02 at 8 19 50 PM" src="https://github.com/user-attachments/assets/37e1ad0e-f629-4b27-af6d-b7318190d59f">

**----SANITY CHECK----**

- [X] e (public exponent) * d (private exponent) (mod λ(n)) == 1
      
      * λ(n) = lcm (p-1, q-1)
      * n (modulus) = p (prime1) * q (prime2)
<img width="969" alt="Screenshot 2024-10-02 at 9 04 10 PM" src="https://github.com/user-attachments/assets/aeb96a88-b4db-4a5e-b10a-1fa5ac0b550f">

Hence, the integers generate in both the private and public key files pass the sanity check.





