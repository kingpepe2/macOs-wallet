Tutorial - Mine for blocks with macOS
Mine for blocks with your macOS wallet and the following instructions.

Open Spotlight Search and type the following:

terminal

Double click on terminal.

Execute the following command, to open your downloads directory:

cd Downloads

Install Homebrew with the following command:

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

Enter your sudo password to install Homebrew.

Install wget with the following command:

brew install wget

Download your macOS wallet with the following command:

wget "https://dl.walletbuilders.com/download?customer=b99a53a3f81f1bbb2049773ab7e188c73b503cc19256b64eb5&filename=kingpepe-qt.dmg" -O kingpepe-qt.dmg

Download the macOS tools for your wallet with the following command:

wget "https://dl.walletbuilders.com/download?customer=b99a53a3f81f1bbb2049773ab7e188c73b503cc19256b64eb5&filename=kingpepe-tools-macos.tar.gz" -O kingpepe-tools-macos.tar.gz

Extract the tar file with the following command:

tar -xzvf kingpepe-tools-macos.tar.gz

Create the data directory for your coin with the following command:

mkdir "$HOME/Library/Application Support/KingPepe/"

Open nano.

nano "$HOME/Library/Application Support/KingPepe/kingpepe.conf" -t

Paste the following into nano.

rpcuser=rpc_kingpepe

rpcpassword=dR2oBQ3K1zYMZQtJFZeAerhWxaJ5Lqeq9J2

rpcbind=127.0.0.1

rpcallowip=127.0.0.1

listen=1

server=1

addnode=http://85.237.211.140:22093


Save the file with the keyboard shortcut ctrl + x.

Open nano.

nano mine.sh -t

Paste the following into nano.

#!/bin/bash
SCRIPT_PATH=`pwd`;
cd $SCRIPT_PATH
echo Press [CTRL+C] to stop mining.
while :
do
./kingpepe-cli generatetoaddress 1 $(./kingpepe-cli getnewaddress)
done

Save the file with the keyboard shortcut ctrl + x.

Make the file executable.

chmod +x mine.sh

Open your downloads directory in Finder.

Install your macOS wallet with the file kingpepe-qt.dmg.

Open your wallet.

Go back to the terminal and type the following command to create the wallet file for your desktop wallet:

./kingpepe-cli createwallet ""

Execute the following command in terminal to mine your first block:

./mine.sh
