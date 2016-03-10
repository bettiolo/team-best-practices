# team-best-practicies

### Cross-team catchup

- (one-time) Introduction to the cross-team catchup
- Each team gives quick updates on what they are working on and plans for next week
   - Granularity of timeline is half a week
- CTO gives company wide updates
- CTO introduces new joiners

### Build/Deployment pipeline
- Push code to github with a dockerfile
- Infra should pick it up, build, test and deploy to dev
- Manual promotion to staging and live
- After each deploy we should have smoke tests / environment tests to check that the deployed instance is working
- Eventually canary deployments to monitor impact of code changes before rolling over all the instances for most critical paths
- A failed deployment to an environment should not kill existing working containers
- Traffic should be routed to new containers while draining connections to old containers
- If a build or promotion breaks, fail loudly

### Platform maintenance
- Regularly go through platform/infrastracture rebuild excercise

### Logging/Metrics
- NGINX should log everything and include the x-tracer (and service name)
- Edge Side Includes should record metrics and log it's own errors and x-tracer
- Apps should record metrics about status codes
- Apps should log errors, warn and info triggered by code
- Apps should log only responses when status code 500+
- elasticsearch/logstash errors caused by malformed application logs should be logged as well and retain the application name field
- Apps should log request tracer (x-tracer)
- Apps should send to downstream APIs the x-tracer header
- Logger should log and write metrics to stdout/stderr
- Docker logging plugin or command line tool should ship to logs and elk
- Docker logging plugin or command line tool should ship metrics to DataDog
- Logger should have a clear api to log x-tracer and error message, additional fields should be logged to a specific property in kibana to avoid name collisions with logstash fields

### Maintenance of nodejs projects
- Assign every project to an active team
- Keep up to date NPM modules (eg. GreenKeeper)
- Keep up to date NodeJS versions
- Use shrinkwrap (To ensure that subsequent builds will happen with same dependency versions)

### New project checklist
- Add deployment info to DataDog
- Add deployment info to NewRelic
- Monitoring on DataDog
- Monitoring on NewRelic
- Monitoring on PingDom
- Create a DataDog dashboard
- Create a NewRelic dashboard
- Ensure metrics flowing to a DataDog
- Ensure logs flowing to Kibana
