# Flask Template

Template repo for deploying a Python Flask app with an Nginx proxy and SSL certificates from Let's Encrypt.

### How to run

Clone the repo:

```
git clone --recurse-submodules https://github.com/lawndoc/web-app-template.git
```

Add your configuration to .env and add it to your environment variables:

```
vim .env
source .env
```

On the first run, initialize the Let's Encrypt certificates with the provided script:

```
./init.sh
```

If the initialization script completed without errors, your containers are running and your app is ready to use. The SSL certs from Let's Encrypt are stored on the host in `./volumes/certbot`. Moving forward, you can use `docker-compose down` and `docker-compose up -d` to stop or start the services.

### Making changes

Don't forget to rebuild the Flask app container after making changes:

```
docker-compose build flask
docker-compose up -d
```
