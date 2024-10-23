*New application (in T3 Stack) = Sonar*
*Current application = Nasus*


### Shared Auth across both applications:
We can use shared JWT decryption with a shared secret. Once a user signs up with Nasus (and since the applications will be deployed on the same domain), Passport will issue a JWT token signed with a secret that will be shared with Sonar for later decryption and attaining the session which can be used to check for role, licenses, etc.

### Maintaining a consistent record of DB migrations between both applications:
- If there are any new migrations in Nasus, we run `drizzle-kit pull` to update Drizzle ORM's client with the new state of our db.
- If there are any new migrations in Sonar, we run `drizzle-kit generate` to generate SQL for migration and that can be run manually or with `db-migrate`. OR, we can just run `drizzle-kit push` to run the migration and generate the SQL ran for that migration which can used for however we wanna keep Nasus in sync.

#### AWS EKS + GitHub Action + NextJS:
[found this dope blog post that fits our case](https://medium.com/@modifyljf/aws-eks-github-action-nextjs-part-1-903165663cb9)
