# The deployment flow is...

0. Code is brought from branches into develop. When ready... (work it out, baby)
1. Code is committed to stage. (manual)
2. Github action runs unit tests and lints. (GHA)
3. Pulumi provisions resources for stages. (GHA)
4. Run post-deploy script for database migration. (in AppPlatform spec?)
5. E2Es run. (GHA)
6. Code is pull requested to master. (GHA? If not, manual)
7. Manual verification of the stage. (manual)
8. Code is merged to master. (manual)
9. New Github action provisions resources for production. (GHA)
10. Run post-deploy script for database migration. (in AppPlatform spec?)
11. Pulumi destroys stage resources. (GHA) (can be easily removed if needed)
12. E2Es run? (GHA)
13. Manual verification of production. (manual)

Gotchas:

- Changing infrastructure and app code on the same commit will not deploy app code (I think?).
