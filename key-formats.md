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

By decoding the contents of my generated public key, I used the **ssh-keygen -f id_rsa_homework.pub -e -m pem > id_rsa_homework.pub.pem** commandline to convert the my public key from OpenSSH to the more generic PKCS#1 PEM file format. I then copy and pasted the contents of id_rsa_homework.pub.pem into the [Michael Holtstrom decoder](http://ldh.org/asn1.html). 

Here is my decoded public key: 

<img width="1049" alt="Screenshot 2024-10-02 at 7 33 16 PM" src="https://github.com/user-attachments/assets/7d9a6f10-e32b-4f6e-88c3-8d5782c72450">

Where, the modulus is the first U.P Integer and the second integer is the exponent (65537 decimal). 

**----Sanity Check----**




