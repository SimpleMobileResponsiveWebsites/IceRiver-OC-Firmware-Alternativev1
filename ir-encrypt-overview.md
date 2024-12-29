The ir-encrypt.sh script is a bash script designed to encrypt and prepare firmware files for IceRiver ASICs. Here's a summary of its functionality, based on the provided source1234:
● Script Usage and Arguments:
○ The script requires four arguments: a background file, a miner file, the target ASIC model, and a version identifier2.
○ An example usage is provided: $0 bg.tar miner.tar ks0pro pbfarmerv12.
○ If the number of arguments is not four, the script will print a usage message and exit2.
○ The script checks if the provided ASIC model is one of the valid models: ks0, ks0pro, ks1, ks2, ks3, ks3m, or ks3l. If the model is invalid, it prints an error message and exits2.
● Directory Navigation:
○ The script changes the current directory to the directory where the script itself is located using cd $(dirname "$(realpath $0)")2.
● Password Handling:
○ It sets two passwords, IRPW0 and IRPW1, as variables2.
○ The password used for encryption, stored in variable IRPW, is determined based on the ASIC model. If the model is ks0pro, then IRPW is set to IRPW1; otherwise, IRPW is set to IRPW02.
● Filename Generation:
○ The script generates three output filenames based on the version identifier and the ASIC model:
■ bgFile: ${4}_bg.bgz2
■ minerFile: ${4}_${3}miner.bgz2
■ upgradeFile: ${4}_${3}update3
● Encryption Process:
○ The script creates a temporary file FSTMP and fills it with 16 bytes of zeros, which is used as a "fake salt"3.
○ Another temporary file CRYPTTMP is created to store intermediate encryption results3.
○ The script encrypts the input background file using openssl with AES-256-CBC and the password stored in the IRPW environment variable. The -nosalt option is used to suppress the inclusion of a random salt, as the fake salt will be prepended in a later step. The encrypted file is written to CRYPTTMP3.
■ The fake salt is prepended to the encrypted background file, and the result is written to /tmp/${bgFile}3.
○ The script then encrypts the input miner file using the same process, prepending the fake salt, and writing the result to /tmp/${minerFile}3.
○ The two encrypted files in /tmp are then archived into a tarball named /tmp/${upgradeFile}.tar4.
○ The tarball is then encrypted using openssl with AES-256-CBC and the password stored in the IRPW environment variable. The encrypted output is written to CRYPTTMP4.
○ The fake salt is prepended to the encrypted tarball, and the final result is written to ${upgradeFile}.bgz4.
○ A message is printed indicating that the ${upgradeFile}.bgz file has been created4.
In summary, this script takes two input files (a background file and a miner file), encrypts them individually using a password determined by the target ASIC model, prepends a fake salt, creates an archive of the encrypted files, encrypts the archive, prepends the fake salt again and outputs an encrypted firmware file with a .bgz extension.
