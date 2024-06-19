# ANUSHKA.S
def caesar_encrypt(text, shift):
    """
    Encrypts the given text using the Caesar Cipher algorithm with the provided shift value.
    
    Parameters:
    text (str): The input text to be encrypted.
    shift (int): The shift value for the Caesar Cipher.

    Returns:
    str: The encrypted text.
    """
    encrypted_text = ""
    
    for char in text:
        if char.isalpha():
            # Handle uppercase letters
            if char.isupper():
                encrypted_text += chr((ord(char) + shift - 65) % 26 + 65)
            # Handle lowercase letters
            else:
                encrypted_text += chr((ord(char) + shift - 97) % 26 + 97)
        else:
            # If it's not an alphabetic character, just add it as is
            encrypted_text += char
    
    return encrypted_text

def caesar_decrypt(text, shift):
    """
    Decrypts the given text using the Caesar Cipher algorithm with the provided shift value.
    
    Parameters:
    text (str): The input text to be decrypted.
    shift (int): The shift value for the Caesar Cipher.

    Returns:
    str: The decrypted text.
    """
    return caesar_encrypt(text, -shift)

def main():
    """
    The main function to run the Caesar Cipher encryption and decryption program.
    """
    while True:
        choice = input("Do you want to (e)ncrypt or (d)ecrypt or (q)uit? ").lower()
        
        if choice == 'q':
            print("Exiting the program.")
            break
        elif choice in ['e', 'd']:
            message = input("Enter your message: ")
            shift = int(input("Enter the shift value: "))
            
            if choice == 'e':
                result = caesar_encrypt(message, shift)
                print(f"Encrypted message: {result}")
            else:
                result = caesar_decrypt(message, shift)
                print(f"Decrypted message: {result}")
        else:
            print("Invalid choice. Please choose 'e' to encrypt, 'd' to decrypt, or 'q' to quit.")

if __name__ == "__main__":
    main()