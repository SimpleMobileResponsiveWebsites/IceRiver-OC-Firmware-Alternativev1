The ir-decrypt.sh script is a bash script designed to decrypt and extract firmware files for IceRiver ASICs1. Here's a summary of its functionality, based on the provided source:

● Script Usage and Arguments:

○ The script requires two arguments: the encrypted firmware file (.bgz) and the target ASIC model2.

○ An example usage is provided: $0 pbfarmerv1_ks0update.bgz ks02.

○ If the number of arguments is not two, the script will print a usage message and exit2.

○ The script checks if the provided ASIC model is one of the valid models: ks0, ks0pro, ks1, ks2, ks3, ks3m, or ks3l. If the model is invalid, it prints an error message and exits2.

● Directory Navigation:

○ The script changes the current directory to the directory where the script itself is located using cd $(dirname "$(realpath $0)")2.

● Password Handling:

○ It sets two passwords, IRPW0 and IRPW1, as variables2.

○ The password used for decryption, stored in variable IRPW, is determined based on the ASIC model. If the model is ks0pro, then IRPW is set to IRPW1; otherwise, IRPW is set to IRPW02.

● Filename Extraction:

○ The script extracts the filename without the path or extension from the provided encrypted file using these steps2:

■ f=${1##*/} removes the path.

■ filename=${f%.*} removes the file extension.

○ The output filename is created by appending .tgz to the extracted filename2.

● Decryption Process:

○ The script creates a new filename variable called encodedFile by appending .enc to the output file name, and then performs the following decryption steps3:

○ A "fake salt" (the first 16 bytes of the input file) is removed using dd and the output is written to the file named by encodedFile3.

■ openssl is used to decrypt the file encodedFile using AES-256-CBC with the password stored in the IRPW environment variable3. 
The decrypted file is saved as outputFile. The -nosalt option is used because the salt is removed from the encrypted file in the previous step3.

■ The encoded file (.enc) is removed after decryption3.

○ A message is printed to indicate the successful creation of the .tgz archive3.

In essence, this script takes an encrypted firmware file, determines the appropriate decryption password based on the target ASIC model, removes the salt, decrypts the file, and outputs a .tgz archive23. The script is designed to work with specific IceRiver ASIC firmware files and models2.
