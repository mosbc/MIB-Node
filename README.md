+ Mined Coins
https://www.mibscan.com/mib_api/mined  

+ Last Block Number
https://www.mibscan.com/mib_api/lastblock  

+ HashRate
https://www.mibscan.com/mib_api/hashrate  

+ Current Number of Miners
https://www.mibscan.com/mib_api/miner  

+ Network Difficulty
https://www.mibscan.com/mib_api/difficulty  
  
Return type: json
Success : {"result_code":200,"result_msg":"Success","result_data":{"difficulty":9416021116104592}}

Failure: {"result_code":500,"result_msg":"Error Message"}

***


# MIB-Node
Extensible full node using MIB v1.8.17



### Supported OS
1. Ubuntu 16.04 LST x64 or later
2. CentOS 7.x x64 or later
3. Windows Server 2012 R2 x64 or later

### Minimum specification for Server
1. Linux / Windows equal 
2. CPU : 2 vcpu or more
3. RAM : 4GB or more
4. DISK : 50GB or more (SSD Recommended)

### Starting Node
1. GMIB  
  -gmib : Run file for Node that constructs MIB Blockchain Network  
  -Default gmib ports for each Network  
   TestNet 35001  
   MainNet 38001  
 
2. Running Normal Node (in Windows)  
  -Run Node for simple blockchain synchronization, input commands below 
   1) TestNet : ***gmib --testnet --datadir /path/to/yourdir***  
   2) MainNet : ***gmib --datadir /path/to/yourdir***  

3. Running Normal Node (in Linux)  
  -Run Node for normal blockchain synchronization 
   1) TestNet : ***$ ./gmib --testnet --datadir /path/to/yourdir*** 
   2) MainNet : ***$ ./gmib --datadir /path/to/yourdir***  
   
   >ex)  
   >$ mkdir -p /home/user/mib/mibnode  
   >$ cd /home/user/mib/mibnode  
   >$ wget ***download URL***/linux/gmib.tar.gz  
   >$ tar xvzf gmib.tar.gz  
   >$ ./gmib --datadir /home/user/mib/data  

4. 4.	Run normal Node Console (in Linux)  
  -Connect to Console after running Node to check the blockchain history  
   ***$ ./gmib --datadir /path/to/yourdir console***  

   >ex)  
   >$ ./gmib --datadir /home/user/mib/data console  
   >Welcome to the Gmib JavaScript console!  

   >instance: Gmib/v1.8.17-stable/linux-amd64/go1.10.4  
   >modules: admin:1.0 debug:1.0 mib:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 smarthash:1.0 txpool:1.0 web3:1.0  

    ***>mib.syncing***  
   > {  
    >currentBlock: 1024,  
    >highestBlock: 3333,  
    >knownStates: 23933,  
    >pulledStates: 23933,  
    >startingBlock: 0  
   > }  
   
    ***>mib.blockNumber***  
    >3333  


### Running Node for Pool Management (on Linux)
Running Node on Pool to enable real Mining
  
1. Uploading Keystore file of Payout Wallet  
  ☞ What is a Payout Wallet? :  
  -A Wallet that is used to distribute Mining reward to Miners (Not a private Wallet)  
  -The Wallet automatically distributes reward to Miners by registering its account in MIB Pool  
  -Save the keystore file and its password after creating the payout wallet from www.mibwallet.com  
   a. Check if you have keystore directory under MIB datadir in Node server (Create it if you don’t have it)  

     >example)  
     >$ mkdir -p /home/user/mib/data/keystore

   b. Upload the keystore file of Payout Wallet in keystore directory that you created from a)  
   
2. Running MIB Node  
  ***$ ./gmib --datadir /path/to/yourdir --port defaultport --rpcport yourport --rpc --rpcaddr 0.0.0.0 --rpcapi “web3,admin,mib,debug,net” --rpccorsdomain*** *  
  
    >example)  
    >$ ./gmib --datadir /home/user/mib/data --port 38001 --rpcport 9999 --rpc --rpcaddr 0.0.0.0 --rpcapi “web3,admin,mib,debug,net” --rpccorsdomain *  
    ☞ Option) add rpcapi if needed  
    -types of rpcapi : web3, admin, mib, debug, net, txpool, personal  

3. Running miner from Node  
  a. Checking Payout Wallet information after running gmib and connecting to RPC Port  
  ***$ ./gmib attach http://ipaddress:rpcport***  
  
    >example)  
    >$ ./gmib attach http://127.0.0.1:9999  
    >Welcome to the Gmib JavaScript console!  

    >instance: Gmib/v1.8.17-stable/linux-amd64/go1.10.4  
    >modules: admin:1.0 debug:1.0 mib:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 txpool:1.0 web3:1.0  

    >  mib.coinbase                                              <<<<<  Check payout wallet address  
    >  “0xaaaaaaa11111112222223333bbbbbb”  
    >  personal.unlockAccount(mib.coinbase, "yourpassword", 0)   <<<<<  Login to use the wallet  
    >  true  
    >  miner.start(1)                                            <<<<<  Start Mining  
    >  null  


### GMIB Main Option  
+Version Check : gmib version  
+Details : gmib --help  

USAGE:
gmib [options] command [command options] [arguments...]

VERSION:  
1.8.17-stable  

|  COMMANDS |  INFO |
|:--------|:--------:|
|**account** | Manage accounts |
|**attach** | Start an interactive JavaScript environment (connect to node) |
|**console** | Start an interactive JavaScript environment |
|**init** | Bootstrap and initialize a new genesis block |
|**version** | Print version numbers |
|**help, h** | Shows a list of commands or help for one command |

|  MIBSMART OPTIONS |  INFO |
|:--------|:--------:|
|**--datadir** | Data directory for the databases and keystore |
|**--keystore** | Directory for the keystore (default = inside the datadir) |
|**--nousb** | Disables monitoring for and managing USB hardware wallets |
|**--networkid value** | Network identifier (integer, 1001=Main, 1002=Test)  (default: 1001) |
|**--testnet** | network: pre-configured proof-of-work test network |
|**--syncmode "fast"** | Blockchain sync mode ("fast", "full", or "light") |

|  PERFORMANCE TUNING OPTIONS |  INFO |
|:--------|:--------:|
|**--cache value** | Megabytes of memory allocated to internal caching  (default: 1024) |

|  ACCOUNT OPTIONS |  INFO |
|:--------|:--------:|
|**--unlock value** | Comma separated list of accounts to unlock |
|**--password value** | Password file to use for non-interactive password input |

|  API AND CONSOLE OPTIONS |  INFO |
|:--------|:--------:|
|**--rpc** | Enable the HTTP-RPC server |
|**--rpcaddr value** | HTTP-RPC server listening interface (default: "localhost") |
|**--rpcport value** | HTTP-RPC server listening port (default: 8545) |
|**--rpcapi value** | API's offered over the HTTP-RPC interface |

|  NETWORKING OPTIONS |  INFO |
|:--------|:--------:|
|**--bootnodes value** | Comma separated enode URLs for P2P discovery bootstrap  (set v4+v5 instead for light servers) |
|**--port value** | Network listening port (default: 30303) |
|**--nat value** | NAT port mapping mechanism  (any|none|upnp|pmp|extip:<IP>) (default: "any") |
|**--nodiscover** | Disables the peer discovery mechanism  (manual peer addition) |

