Akash Week 2 Challenge 1 Process



The process is the same as last week, submit deployment and submit json. Use deploy-2-1.yaml to deploy akash on akash.

To note the version has been updated from r11 to r13, to enter akash versionto see the old version is to update it.

There are two ways to update, one is to cut to the akash source folder, pull the new code and remake

```
cd $GOPATH/src/github.com/ovrclk/akash
git pull origin v0.9.0-rc13
make deps-install
make install
```

The other is to download the official compilation directly

```
wget https://github.com/ovrclk/akash/releases/download/v0.9.0-rc13/akash_0.9.0-rc13_linux_amd64.zip
sudo apt install unzip
unzip akash_0.9.0-rc13_linux_amd64.zip
mv akash_0.9.0-rc13_linux_amd64/akash go/bin/akash
```



The Mac update method is  `brew upgrade akash-edge`

After the update is complete with  `akash version` confirmation

The rest of the steps are the same as the first week. Generate json and submit it to the ecosystem library, just submit a pull request. Refer to https://github.com/StephenPan/Akash-Challenge-3-process-akash-node   

In the ecosystem library, you may need to merge the source remote branch first when pushing, you can use the following command: add the source master branch, pull it to the local master, and then merge the master



```
git remote add source https://github.com/ovrclk/ecosystem.git
git fetch source master
git merge source/master
```

```


```



**That's it, it's easy, now go ahead and try it and complete your own Akash mission.**












To make it easier for beginners to complete the challenges, you can also refer to the following.





### Installations:

- git clone https://github.com/blurtbuzz/Akash-Challenges.git
- cd Akash-Challenges
- . ./setup.sh

### Setup Wallet:

- export KEY_NAME="ANY_KEY_NAME"
- export KEYRING_BACKEND="os"
- export ACCOUNT_ADDRESS="$(akash keys show $KEY_NAME -a)"

### Deploy Your App:

- cd
- cd ecosystem

- git remote add upstream https://github.com/ovrclk/ecosystem.git
- git fetch upstream
- git pull upstream master

- curl -s https://raw.githubusercontent.com/ovrclk/docs/02995cca8d90a6bdf1bec896c6e28b6e51cb58ee/testnet-challenges/deploy-2-1.yaml > deploy.yml

- akash tx deployment create deploy.yml --from $KEY_NAME --node $AKASH_NODE --chain-id $AKASH_CHAIN_ID -y

- akash query market lease list --owner $ACCOUNT_ADDRESS --node $AKASH_NODE --state active

  - Wait for your Lease

  leases:

  - lease_id: dseq: "47714" gseq: 1 oseq: 1 owner: akash1nyxtwy6y0crnvrfmctfjyaljzu8y4xc46398ah provider: akash174hxdpuxsuys9qkauaf57ym5j8dm4secnz6jd7 price: amount: "43" denom: uakt state: active pagination: next_key: null total: "0"

- export DSEQ=GENERATED_VALUE_FROM_ABOVE

- export GSEQ=GENERATED_VALUE_FROM_ABOVE

- export OSEQ=GENERATED_VALUE_FROM_ABOVE

- export OWNER=GENERATED_VALUE_FROM_ABOVE

- export PROVIDER=GENERATED_VALUE_FROM_ABOVE

- Go to https://app.akash.network/

- Go to Earn Token Rewards and copy the Participant Code

- export CODE=YOUR_PARTICIPANT_CODE

- akash query market lease get --dseq $DSEQ --gseq $GSEQ --oseq $OSEQ --provider $PROVIDER --owner $ACCOUNT_ADDRESS --node $AKASH_NODE -o json > akashian/phase3/challenge4/$CODE.json

- Commit your change and make a pull request



For more information about Akash, please use the following links to learn more.



Official Website: https://akash.network/?lang=zh-hans  

Twitter: https://twitter.com/akashnet_   

Telegram: https://t.me/AkashNW    



  