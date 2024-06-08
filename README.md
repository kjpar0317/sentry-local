# Sentry 9 (Old version)

1. Change SENTRY_SECRET_KEY to random 32 char string
2. Run

```
docker-compose up -d
```

3. Run

```
docker-compose exec sentry sentry
```

upgrade to setup database and create admin user

4. (Optional)

```
Run docker-compose exec sentry pip install sentry-slack
```

if you want slack plugin, it can be done later 5. Run

```
docker-compose restart sentry
```

6. Sentry is now running on public port 9000

# Linux (Sentry latest, heavyweight.... but )

- Session Replay shows you a video-like reproduction of your user sessions using the rrweb recording library.
- Session recordings show every user interaction in relation to network requests, DOM events, and console messages.
- Fingerprints error events based on information like stack trace, exception, and message. Transaction events are fingerprinted by their spans.
- Ability to forward processed error events to certain third-party providers, such as Segment and Amazon SQS
- Segment integration will generate Error Captured events within your data pipeline. These events will only be captured for error events and only when an ID is present.
- Inbound data filters allow you to determine which errors, if any, Sentry should ignore. Filters include known web crawlers, browser extension errors, events from localhost, and known browser legacy errors.

Minimum system specification for running Sentry looks like this:

- 2 CPU cores
- 4 GB RAM

Current recommended system specification for running Sentry is:

- 4 CPU cores
- 16 GB RAM
- 20 GB free disk storage space

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

# Glitchtip (lightweight Sentry alternative)

- Recommended system requirements: 1GB RAM, x86 or arm64 CPU
- Minimum system requirements: 512MB RAM + swap

```
cd glitchtip
docker-compose up -d
```
