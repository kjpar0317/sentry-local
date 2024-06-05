# Windows (only Sentry 9)

1. Change SENTRY_SECRET_KEY to random 32 char string
2. Run docker-compose up -d
3. Run docker-compose exec sentry sentry upgrade to setup database and create admin user
4. (Optional) Run docker-compose exec sentry pip install sentry-slack if you want slack plugin, it can be done later
5. Run docker-compose restart sentry
6. Sentry is now running on public port 9000

# Linux (Sentry latest)

1. install

```
git clone https://github.com/getsentry/self-hosted.git
SENTRY_SELF_HOSTED_HOME=`pwd`/self-hosted
cd $SENTRY_SELF_HOSTED_HOME
./install.sh
or
./install.sh --skip-user-creation
"""output
...
Would you like to create a user account now? [Y/n]: y
Email: 'input admin email'
Password: 'input admin password'
Repeat for confirmation: 'input admin password'
...
```

2. sentry cluster execute

```
cd $SENTRY_SELF_HOSTED_HOME

#  set sentry enviorment
cp .env .env.custom
vi .env.custom

""" set custom port
SENTRY_BIND=9000
"""

# sentry cluster execute
docker-compose --env-file .env.custom up -d
```

3. sentry cluster exit

```
cd $SENTRY_SELF_HOSTED_HOME
docker-compose down
```
