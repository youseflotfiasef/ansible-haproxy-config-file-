# latest-version-full-node-code with <<python>>

import os, sys
import re
import json
from typing import Any
import requests
from http_parser.parser import HttpParser

def replace_last(source_string, replace_what, replace_with):
    head, _sep, tail = source_string.rpartition(replace_what)
    return head + replace_with + tail

urls = {
    'cardano':'https://github.com/input-output-hk/cardano-node/releases/latest',
    'walletcardano':'https://github.com/input-output-hk/cardano-wallet/releases/latest',
    'bsc':'https://github.com/binance-chain/bsc/releases/latest',
    'bc':'https://github.com/gavinhoward/bc/releases/latest',
    'teron':'https://github.com/tronprotocol/java-tron/releases/latest',
    'litecoin':'https://github.com/litecoin-project/litecoin/releases/latest',
    'ethereum':'https://github.com/ethereum/go-ethereum/releases/latest'
}

versions = []
for index,value in enumerate(urls):
    res = requests.get(urls.get(value))
    urlPaths = res.url.split("/")
    versions.append(value + ":" + urlPaths[len(urlPaths)-1])
   
f = open('/home/y.lotfiasef/Documents/version_now'+".txt", 'r')

print(versions)
result = ""
for i,v in enumerate(f):
    v = v.replace("\n","")
    if v != versions[i]:
        print("no")
        result = result + (versions[i] + "\n")
        print("telegram bot message ")
    else:
        result = result + (v + "\n")

print(result)
f.close()
w = open('/home/y.lotfiasef/Documents/version_now'+".txt", 'w')
w.write(result)
w.close()

###################################################################

q = open('/home/y.lotfiasef/Documents/version_now'+".txt", 'w')
q = [line.rstrip('\n') for line in q]

q.close()
