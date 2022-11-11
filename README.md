

# Description

This is the repo for the Sharing-UI of project Anomura.

Some endpoints which post a message to a discord server, we need a nodejs server to handle discordjs package, currently we cannot have discordjs within this repo due to Vercel only supports Node runtime execution up to v14 at the time of development. Discordjs needs v16.

Vercel Deployment

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/qhuynhvhslab/test&env=DATABASE_URL,NEXTAUTH_URL,NEXT_PUBLIC_NEXTAUTH_SECRET,NEXT_PUBLIC_INFURA_ID,NEXT_PUBLIC_ENABLE_CHALLENGER&envDescription=Postgresql%Db,URL%20For%20Next-Auth,Enter%20Your%20Next-Auth%20Secret%20Key,Infura%20For%20Login,Enable%20Challenger)

```
INSERT INTO public."Admin" (id, wallet, nonce) VALUES (1, 'ENTER YOUR WALLET HERE', '123456789123456789');

INSERT INTO public."QuestType" (id, name, description) VALUES (1, 'Discord Authenticate', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (2, 'Twitter Authenticate', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (3, 'Follow Twitter Account', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (4, 'Follow Instagram Account', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (5, 'Retweet a Tweet', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (6, 'Anomura #SUBMISSION Quest', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (9, 'Limited Free $SHELL', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (10, 'Join our Discord', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (11, 'Free $SHELL On Collaboration', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (12, 'Daily Shell Quest', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (13, 'Code Quest', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (14, 'Wallet Authenticate', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (15, 'Claim Reward For Owning NFT', NULL);
INSERT INTO public."QuestType" (id, name, description) VALUES (16, 'Unstoppable Domain Authenticate', NULL);

INSERT INTO public."RewardType" (id, reward) VALUES (1, '$Shell');
INSERT INTO public."RewardType" (id, reward) VALUES (2, 'Mint List');
```

## How to use

<details>
  <summary> Setup database</summary>
 
-------------------
  ### Modify env file (.env.development)
```js
     DATABASE_URL=postgres://username:password@localhost:5432/database_name
```
  ### Apply prisma migration
```js
      dotenv -e .env.development -- npx prisma migrate dev
```

### Expected: 
In any sql client, the tables should be created.


  ### Populate data
Go to ./prisma/seed/admin.js
Modifying the value with your wallet, then execute these commands:
```js
dotenv -e .env.development -- node ./prisma/seed/admin.js
dotenv -e .env.development -- node ./prisma/seed/quest-type.js
dotenv -e .env.development -- node ./prisma/seed/reward-type.js 

```

</details>
<br/>

<details>
  <summary> Start up</summary>
 
  ### Modifying BasePath
This project is configured with basepath in order to be accessed as sub domain from another repository so the default starting path would be
http://localhost:3000/[base_path_name] (http://localhost:3000/challenger)

If we use this repos as the standalone we would have to remove all the basePath value.
- Under next.config.js
- Under enums/
- Under sass/  (anything with /[base_path_name]) 

### Start the project
```js
npm run dev
```

Go to admin site on
http://localhost:3000/challenger/admin

Create quest 
Under http://localhost:3000/challenger/admin/quest

- Join Discord Type: server should be name of server (anomuragame, atarix,...)
- Discord Authenticate (Link current session with discord)
- Twitter Authenticate (Link current session with twitter)
- Twitter Retweet
- Twitter Follow
- Instagram Follow
- Wallet Authenticate
- Code Quest
- Image Upload
- Daily
- Claim Reward for owning NFT

</details>
