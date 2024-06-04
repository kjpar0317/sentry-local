1. Change SENTRY_SECRET_KEY to random 32 char string
2. Run docker-compose up -d
3. Run docker-compose exec sentry sentry upgrade to setup database and create admin user
4. (Optional) Run docker-compose exec sentry pip install sentry-slack if you want slack plugin, it can be done later
5. Run docker-compose restart sentry
6. Sentry is now running on public port 9000
