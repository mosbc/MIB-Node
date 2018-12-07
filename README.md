# MIB-Node
Extensible full node using MIB v1.8.17



### Supported OS
1. Ubuntu 16.04 LST x64 or more
2. CentOS 7.x x64 or more
3. Windows Server 2012 R2 x64 or more

### Minimum Server Requirements
1. For Linux / Windows 
2. CPU : 2 vcpu or more
3. RAM : 4GB or more
4. DISK : 50GB or more (SSD Recommended)

### On Running Node
1. GMIB  
  -gmib : node executable for MIB Blockchain Network  
  -Default gmib ports  
    TestNet   35001  
    MainNet  38001  

2. Running Normal Node (on Windows)  
  -Running Normal Node for simple Blockchain synchronization  
   ***gmib --datadir /path/to/yourdir***  

3. Running Normal Node (on Linux)  
  -Running Normal Node for simple Blockchain synchronization  
   ***$ ./gmib --datadir /path/to/yourdir***  
   
   >ex)  
   >$ mkdir -p /home/user/mib/mibnode  
   >$ cd /home/user/mib/mibnode  
   >$ wget ***download URL***/linux/gmib.tar.gz  
   >$ tar xvzf gmib.tar.gz  
   >$ ./gmib --datadir /home/user/mib/data  

4. Running Normal Node for Console (on Linux)  
  -Running Node and connecting to Console to check Blockchain history  
   ***$ ./gmib --datadir /path/to/yourdir console***  

   >ex)  
   >$ ./gmib --datadir /home/user/mib/data console  
   >Welcome to the Gmib JavaScript console!  

   >instance: Gmib/v1.8.17-stable/linux-amd64/go1.10.4  
   >modules: admin:1.0 debug:1.0 mib:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 smarthash:1.0 txpool:1.0 web3:1.0  

   > mib.syncing  
   {  
     currentBlock: 1024,  
     highestBlock: 3333,  
     knownStates: 23933,  
     pulledStates: 23933,  
     startingBlock: 0  
   }  
   > mib.blockNumber  
   3333  
