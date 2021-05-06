Zbank
Below are the steps taken for setting up and running the nodes on the blockchain 

MyCrypto wallet opened using secret key, terminal launched and cd(ed) into a Zbank directory

Two new nodes were then generated (to serve as our pre-approved sealer addresses) for the network with a separate datadir for each using geth using the following commands 
./geth --datadir node1 account new
./geth --datadir node2 account new

Next genesis block was generated using ./pupeth command choosing PoA (Proof of Athority) algorithm
Network account name is "pup1", chain network id is 2021, first Node address is to Seal, Account prefunded is the existing MyCrypto address
Exported genesis configuraiton chose pup1.json

Initialized the nodes with the genesis' json file using geth with pup1.json
./geth --datadir node1 init pup1.json
./geth --datadir node2 init pup1.json

Both Nodes were started by the following commands 
./geth --datadir node1 --unlock "0bBF1aA4b52Dc07cA07a0947941556c1FF895860" --mine --rpc --allow-insecure-unlock

./geth --datadir node2 --unlock "e1c927b11C23BA049015a09B24628277425D4526" --mine --port 30304 --bootnodes "enode://984afe0a6bacabe4fbe63feeb587d0602d9d3c610852aa642fd8b1c5b1bb1975662734a622a7b4e42156b0e0fcf51646ddbdbce3aeb558f5f18703657b2e432d@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

Once blockchain was running it was connected to MyCrypto for testing
Custom Node "pup1" was set up and tested by sending money between accounts 

To start the blockchain (in separatewindows)
./geth --datadir node1 --unlock "0bBF1aA4b52Dc07cA07a0947941556c1FF895860" --mine --miner.threads 1 --allow-insecure-unlock 

./geth --datadir node2 --unlock "e1c927b11C23BA049015a09B24628277425D4526" --mine --port 30304 --bootnodes "enode://984afe0a6bacabe4fbe63feeb587d0602d9d3c610852aa642fd8b1c5b1bb1975662734a622a7b4e42156b0e0fcf51646ddbdbce3aeb558f5f18703657b2e432d@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock --rpc

Geth a command line interface that allows us to run a full Ethereum node.  If allows us will allow us to mine blocks , generate ether, deploy and interact with smart contracts , transfer funds , block history inspection and create accounts etc..

--datadir node takes us to nodes directory

--unlock "node address" allows to gain access using node's public key

-- mine commandline flags to mine

--miner.threads  used to set the number parallel mining threads, Number of CPU threads to use for mining

--allow-insecure-unlock  allowed insecure account unlocking when account-related RPCs are exposed by http
 
 
--port 30304     port is uised for internal communicaton between wallet and geth

--rpc  rpc interface interacts with json argument enables the HTTP-RPC server, starts the HTTP JSON-RPC protocol, which defines several data structures and the rules around their processing,

"enode://984afe0a6bacabe4fbe63feeb587d0602d9d3c610852aa642fd8b1c5b1bb1975662734a622a7b4e42156b0e0fcf51646ddbdbce3aeb558f5f18703657b2e432d@127.0.0.1:30303"     Ethereum node in the form of a URI         

--bootnode takes part in the network node discovery protocol, but does not run any of the higher level application protocols. It can be used as a lightweight bootstrap node to aid in finding peers in private networks.

--ipcdisable   Disables the IPC-RPC server