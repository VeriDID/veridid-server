
## Installation on AWS or local
Setup a t2.medium EC2 instance with Ubuntu 22.04, 20GB disk, and open up ports 3000, 8000

```bash
// Get latest Node.js and npm environment
sudo apt update
sudo apt upgrade
sudo apt install nodejs
sudo apt install npm
sudo npm install -g n
sudo n latest
sudo npm install npm@latest -g
```

```bash
// Build libindy.so
sudo apt install pkg-config
sudo apt install curl build-essential gcc make -y
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
// May require shell restart
sudo apt install pkg-config
sudo apt -y install libsodium-dev
sudo apt install libzmq3-dev

git clone https://github.com/hyperledger/indy-sdk.git
cd ./indy-sdk/libindy
cargo build --features sodium_static
sudo mv target/release/libindy.so /usr/lib/libindy.so
cd ../..
```

```bash
git clone https://github.com/VeriDID/afj-test.git
cd afj-test
npm install
npm run start:dev
```
```bash
http://YOUR_PUBLIC_IP:3000/api
```

### Additional information for Ubuntu users: 
If there is an error: "failed to run custom build command for openssl-sys v0.9.59"
```
# Edit file: cargo.toml  (inside the folder “indy-sdk/libindy”)
openssl = { version = "0.10", features = ["vendored"] }
$ cargo build --features sodium_static
$ sudo mv target/debug/libindy.so /usr/lib/libindy.so
$ cd ../..

# Run below command to ensure indy-sdk is properly installed 
(Select YES for any additional package installation)
$ npx -p @aries-framework/node is-indy-installed

```
## Running the app

```bash
# development
$ yarn start:dev
```
