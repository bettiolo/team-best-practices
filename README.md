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
