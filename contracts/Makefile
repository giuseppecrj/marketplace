# include .env file and export its env vars
# (-include to ignore error if it does not exist)
-include .env

# Update dependencies
all: clean install update build

install 			:; forge install
setup					:; make update-libs ; make install-deps
update-libs		:; git submodule update --init --recursive
install-deps	:; yarn install --frozen-lockfile
solc					:; nix-env -f https://github.com/dapphub/dapptools/archive/master.tar.gz -iA solc-static-versions.solc_0_8_13
remappings 		:; forge remappings > remappings.txt

# Build & test & deploy
node 						:; yarn hardhat node
account         :; yarn account
generate        :; yarn generate

build         	:; forge build
clean        		:; forge clean
update        	:; forge update
lint          	:; yarn run lint
test          	:; forge test
test-gasreport 	:; forge test --gas-report

# test-fork     :; forge test --gas-report --fork-url ${ETH_NODE}
watch		  			:; forge test --watch src/
