
# Required:
Docker, 
GO lang, 
Node 16


# Network Startup

cd test-network

./network.sh up createChannel -c mychannel -ca

./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-typescript/ -ccl typescript


# Backend Startup

cd asset-transfer-basic/rest-api-typescript

TEST_NETWORK_HOME=../../test-network npm run generateEnv

export REDIS_PASSWORD=$(uuidgen)
npm run start:redis

npm run build

npm run start:dev
