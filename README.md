# **AWS build specification**

**AWS build specification URL**

https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html

**Summary Notes:**

1. Version use 0.2 as default

[version](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html#build-spec.version): 0.2 **(Mandatory)**

2. run-as (optional)

3. env (optional)

   To prevent sensitive keys from being logged in Cloudwatch logs

4. env/shell (optional)

   For Linux operating systems, supported shell tags are:

   - `bash`
   - `/bin/sh`

5. Env/variables (optional)

   Contains a mapping of `key`/`value` scalars

   6. env/parameter-store (optional)

Required if `env` is specified, and you want to retrieve custom environment variables stored in Amazon EC2 Systems Manager Parameter Store. Contains a mapping of `key`/`value` scalars. To allow CodeBuild to retrieve custom environment variables stored in Amazon EC2 Systems Manager Parameter Store, you must add the `ssm:GetParameters` action to your CodeBuild service role.

7. Env/secrets manager (optional)

   Required if you want to retrieve custom environment variables stored in AWS Secrets Manager. Specify a Secrets Manager `reference-key` using the following pattern:

   ```yaml
   <key>`: `<secret-id>:<json-key>:<version-stage>|<version-id>
   ```

8. env/exported-variables (optional)

   Exported environment variables are used in conjunction with AWS CodePipeline to export environment variables from the current build stage to subsequent stages in the pipeline. 

9. env/git-credential-helper (optional)

10. proxy (optional)

11. phases (**Mandatory**)

**Notes: if you have install commands at a minimum, either you can use at a minimum 'phases/install/commands' . The other option is to use 'Phases/build' and 'phases/build/commands'. Everything else in phases seem to be optional.**

12. phases/*/run-as (optional)
13. phases/*/on-failure (optional)
14. phases/*/finally (optional)
15. phases/install/runtime-versions (optional)
16. phases/install/commands (optional)
17. phases/pre_build (optional)
18. phases/pre_build/commands (required only if phases/pre_build is present)
19. phases/build (optional)
20. phases/build/commands (required only if phases/build is present)
21. phases/post_built (optional)
22. phases/post_build/commands (required only if phases/post_build is present)
