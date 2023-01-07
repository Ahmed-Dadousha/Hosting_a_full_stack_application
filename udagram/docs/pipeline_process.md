## Pipeline

From the root of the project:
- `npm run frontend:install`    - To install frontend dependencies.
- `npm run frontend:build`      - To build the Angular/Frontend.
- `npm run api:install`     - To install backend dependencies.
- `npm run api:build`       - To transpile the Typescript/Backend.
- `npm run frontend:deploy`       - To deploy frontend.
- `npm run api:deploy`       - To deploy Typescript/Backend.

#### CircleCI
CircleCI reads the `.circleci/config.yml` file, which instructs the service on what to perform. In the example of Udagram, CircleCI will perform two tasks (frontend and backend configuration).
- **Frontend**: Executes the `build` script from the `package.json` file. Then, using the AWS CLI, upload assets to S3.
- **Backend**: Executes the `build` script, exports all CircleCI configuration environment variables to a `.env` file, and then runs the `deploy` script. The archive is then uploaded to S3 using AWS CLI.

Setup the following variables in the .env file or in the cloud environments:
```
- URL                 = <Url>
- JWT_SECRET          = <Any_PassPhrase>
- AWS_REGION          = <us-east-1>
- AWS_PROFILE         = <Profile>
- AWS_BUCKET          = <Bucket_Name>
- PORT                = <your port>
- POSTGRES_HOST       = <Database_IP_Address>
- POSTGRES_PORT       = <Database_Port>
- POSTGRES_DB         = <Database_Name>
- POSTGRES_USERNAME   = <Database_Username>
- POSTGRES_PASSWORD   = <Database_Password>

```
## Testing
1. `cd udagram-frontend`
2. `npm run test`  