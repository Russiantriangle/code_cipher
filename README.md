# code_cipher
import math

# Create List of Characters
alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']

# Ask user to input required information

direction = input("Type 'encode' to encrypt, type 'decode' to decrypt:\n")
text = input("Type your message:\n").lower()
shift = int(input("Type the shift number:\n"))
 


#function to encrypt the message 
def encrypt(text,shift):
    #transform string into a list
    list1 = list(text)
    #create a blank list
    empty_list = []
    #loop to shift the letter by the given number
    for count in range(0,len(text)):
        #checking if the given character in our alphabet
        if list1[count] in alphabet:
            #finding the index in the alphabet of the given letter in the word
            index_letter = alphabet.index(list1[count])
            #shifting the index by the users number
            updated_index = index_letter + shift
            #if index is higher than the number of letters in the alphabet then bring it back to the number of letters in the alphabet
            if updated_index > len(alphabet) - 1:
                #number of time the shift is bigger than number of letters in alphabet
                n = math.floor(updated_index/(len(alphabet) -1))
                #bring it back to the number of letters in the alphabet
                updated_index = updated_index -n * len(alphabet)
            #fill the empty sting with characters
            empty_list.append(alphabet[updated_index])
        else:
            empty_list.append(list1[count])
    #convert from list to string
    updated_word = ''.join(empty_list)
    print(updated_word)


def decrypt (text, shift):
    list1 = list(text)
    empty_list = []
    for count in range(0,len(text)):
        if list1[count] in alphabet:
            index_letter = alphabet.index(list1[count])
            updated_index = index_letter - shift
            if updated_index < -1*len(alphabet):
                n = math.floor(-updated_index/(len(alphabet) -1))
                updated_index = updated_index +(n+1) * len(alphabet)
            empty_list.append(alphabet[updated_index])
        else:
            empty_list.append(list1[count])
    updated_word = ''.join(empty_list)
    print(updated_word)

if direction == 'encode':
    encrypt(text,shift)
else:
    decrypt(text, shift)
