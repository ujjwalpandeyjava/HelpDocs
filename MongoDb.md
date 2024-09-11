# Install MongoDB

`https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-os-x/`

## Install the Xcode
xcode-select --install

## Install brew
Install brew using the official Homebrew installation instructions.

## Installing MongoDB 7.0 Community Edition
brew tap mongodb/brew
brew update
brew install mongodb-community@7.0



## To run MongoDB (i.e. the mongod process) as a macOS service, run:
brew services start mongodb-community@7.0

## To stop a mongod running as a macOS service, use the following command as needed:
brew services stop mongodb-community@7.0

## To run mongod manually as a background process using a config file, run:
For macOS running on Apple Silicon processors:

`mongod --config /opt/homebrew/etc/mongod.conf --fork`

## To run mongod manually as a background process specifying --dbpath and --logpath on the command line, run:

`mongod --dbpath /path/to/dbdir --logpath /path/to/mongodb.log --fork`

To stop a mongod running as a background process, connect to the mongod using mongosh, and issue the shutdown command as needed.
