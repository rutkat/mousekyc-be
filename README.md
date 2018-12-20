# mousekyc-be
This is the back end service running on node.js with mongodb, installed with docker.
[Click here to see the project description.](https://github.com/norestlabs/mousekyc)

## Installation Instructions
***Prerequisites:*** Please ensure you have Node.js v8 or higher and Docker v18.06.1 or higher installed. [Mailgun](https://www.mailgun.com/) will be needed for the email messaging service. The docker setup includes mongoDB without additional database installation.

1. Clone the repo and install dependencies:
```
git clone https://github.com/norestlabs/mousekyc-be.git
npm install
```
2. Modify server configuration in `src/config/default.js`. `db` is to choose the local or docker mongoDB. `email` is for providing your mailgun credentials. `baseUrl` is to choose your localhost server or mousebelt's.

3. Ensure Docker is running and execute the command:
`docker-compose up`

4. Leave the current terminal open, and in new terminal window you can see the processes running with the command:
`docker ps -a`

5. Now you can proceed with the [mousekyc-fe](https://github.com/norestlabs/mousekyc/mousekyc-fe) and [mousekyc-admin](https://github.com/norestlabs/mousekyc/mousekyc-admin) repos.


### Alternative setup
If you prefer not to use docker or have a port conflict, you should manually install MongoDB.
1. Once you have downloaded and installed MongoDB from [https://www.mongodb.com/download-center/community](https://www.mongodb.com/download-center/community)
2. You will have to create and run an instance in a separate terminal window. See details here
[https://docs.mongodb.com/manual/tutorial/manage-mongodb-processes/](https://docs.mongodb.com/manual/tutorial/manage-mongodb-processes/)
3. Update the config setting on line 3, file `src/config/default.js` to use the local db `db: 'mongodb://localhost:27017/kyc-db'`

4. Run mongodb and start the app:
```
mongod
npm start
```

### Configuration
Copy and rename the backup js files extension in the config folder. Modify the following files to suit your needs.
```
src/config/development.js.bak
src/config/production.js.bak
src/config/test.js.bak
```

### Run a test scenario

`docker-compose -f docker-compose.test.yml up`

Check output results with:
`curl -i http://localhost:3000/global/countries`

### For Production Use
```
npm install
pm2 start pm2.json
# Restart server
pm2 restart mousekyc-backend
```


### Documentation
[**API Docs**](https://github.com/norestlabs/mousekyc-be/wiki) can be found inside the repo wiki.
