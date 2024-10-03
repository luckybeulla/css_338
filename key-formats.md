***Lucky Beulla Muhoza***

***CS 338***

***Prof. Jeff Ondich***

## SSH KEY FILE FORMATS ##
**Private Key** 

The private key is expected to contain the following items as per [Appendix 1.2 of RFC 8017](https://datatracker.ietf.org/doc/html/rfc8017#appendix-A.1.2), the private key is expected to contain the following integers: 

<img width="781" alt="Screenshot 2024-10-02 at 11 36 10 AM" src="https://github.com/user-attachments/assets/8aa13e81-ab67-471e-89a1-7a3484a8e8cd">

After I generated my private key using the **ssh-keygen -t rsa -m pem** commandline, I copyied the contents of the file containing the private key to my clipboard (cat id_rsa_homework | pbcopy) and pasted them into the [Lapo Luchini ASN1 decoder](https://lapo.it/asn1js/). 

The decoded elements of my private key are: 

<img width="932" alt="Screenshot 2024-10-02 at 11 37 38 AM" src="https://github.com/user-attachments/assets/a27ff689-ff63-458c-8fd9-985a98f124aa">
