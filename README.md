# Decoder_with_Jump_Table
Using the simulator "Visual" to represent Assembly Language Programming.  Created a basic decoder to pass a message with a jump table


**HW7 – Assembly Language Programming – due date April 2nd (sent by email)**

**1.	The objective of the assignment is to practice the Jump (branch) table technology, that is used as a programming decoder (like switch in high-level programming languages) to call a subroutine from a significand list of subroutines. See the Jump.s code, which is accompanying this assignment. 


       The program must implement light weight symmetric cryptography based on XOR operations and permutations. In symmetric cryptography both partners (two application programs Alice and Bob) share a secret key, which is just a binary sequence. Alice uses the key to encrypt a message and sends the encrypted message to Bob. Bob receives the message and uses the same key to decrypt the message.
 
 
**2.	Short description of the program functions:

	A message is given in four words with packed ASCII symbols (4 symbols in every word). Every word (4 ASCII symbols) is encrypted by word rotation (depends on the key) and bitwise XOR operation with a 32-bit key.  As a result, the message is encrypted. 
	
A Jump table has to be used for the rotation operation. The rotation cases depend on the key:

-	Case 0: If the key is a “negative” number, move 0 in a case register (for example r7);
-	Case 1: If the key is a “positive” number, move 1 in the case register r7;
-	Case 2: If the key is positive and greater than 0x00001000, move 2 in the case register r7;
-	Case 3: If the key is negative less than 0xF0000000, move 3 in the case register r7.

According to the case value call (jump) to the rotation subroutine
After return from the rotation subroutine perform XOR with the key.
	The decryption process (bitwise XOR with the key and backward rotation) is performed again over every word, which produces the decrypted message. 
	At the end, the program compares in a separate subroutine the original and the decrypted message to check the correctness of the encryption algorithm.  

**3.	The structure of the program is a student’s choice but jump table technique is required to be implemented. Here is one exemplary structure:


•	Select a message, 16 symbols and declare it by DCD in 4 words.
•	Select a 32-bit key.
•	The main subroutine calls in a sequence the encryption subroutine, the decryption subroutine and the compare subroutine.
•	The encryption subroutine makes word after word first some rotation using jump table to the case subroutines: case 0 is to rotate ROR 4, case 2 - rotate ROR 8, case 3 - ROR 12, case 4 - ROR 16. After return from rotation every word is XOR-ed with the key and generates the encrypted message. The encryption subroutine should not destroy the original message.
The decoding follows the reversed sequence. 
•	The decryption subroutine for every word of the encrypted message makes first XOR with the key and after that backward rotation (estimate the number of RORs). As a result, generates the decrypted message. 
•	The comparison subroutine compares the original and decrypted messages. 

