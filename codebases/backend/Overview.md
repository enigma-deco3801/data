# Travikit Backend Overview
## Getting Started
At the time of writing this, this is the stack of the Travikit Backend: 
**TLDR:** TypeScript based node server using the GraphQL protocol. It was bootstrapped using express and apollo, and is powered by a MySQL database. 
- **`Node` with `TypeScript` :** TypeScript is being used because it is compiled, and a superset of JavaScript, so we can take advantage of JavaScript's modular syntax. It also supports all the latest JS standards ahead of the browser and Node LTS while at the same time maintaining backwards compatibility. Since you know the type of each data structure, auto complete support by the IDE is first class. 
-  **`Planetscale` :** Database host & provider. Allows us to branch out databases just like we branch out the source code on GitHub. Uses MySQL behind the scenes. 
- **`AWS S3` :** Media storage host & provider
- **`AWS EC2` / `Heroku` :** Server hosting
- **`Prisma` :** Used for Object Relational Modelling / Mapping. Instead of writing raw SQL queries, we can call functions like `prisma.user.findOne({where: email})` which is more secure and readable. These ORMs make CRUD very easy and handle most performance and security related aspects of interfacing with a database. Prisma has out of the box `typescript`  support. You do not need to define types manually. `Prisma` generates them for you. That's where it shines. You just have to define the schema in the syntax that they have provided. The `typegraphql-prisma` plugin is used as well to generate GraphQL query and mutation types.
- **`Jest` :** Go to testing library.
- **`Express` :** Bootstrapping a `node` based server.
- **`Apollo Server Express` :** Bootstrapping and configuring a `graphql` Server. 
- **`TypeGraphQL` :** Declaratively defining the graph schema, including types, interfaces, enums, unions and subscriptions

### 1. Setting up the development environment
#### 1.1 Prerequisites 
- Install Visual Studio Code. Install extensions for `ESLint` and `Prisma`, along with any others like you want. It is highly recommended that you enable `Auto Save` on VS Code. Also enable GitHub Copilot and VS Code Intellisense if you haven't. All these tools come as extensions, so just search the marketplace. 
- Install `node` if you haven't already. It is highly recommended that you install it through `nvm` or `volta`. This makes upgrading Node easier. A quick google will help you understand what these technologies are. Primer for this is out of scope. 
- Install `yarn` - a package manager which serves as an alternative to `npm`. Vishal has made a `yarn` primer for you - [[Yarn Primer]].
- `npm i -g yarn`: Install yarn
- `npm i -g eslint`: Helps with linting on VS Code

#### 1.2 Dev Setup 
- Clone the project `travikit-backend` - https://github.com/enigma-deco3801/travikit-backend
- Run: `cd travikit-backend`
- Run: `yarn`
- Copy the `.env.sample` and rename it to `.env`. All sensitive credentials go here. Never commit this to the repository. By default, `.env` has been added to the `.gitignore`.
  *⚠️ **Note:** Contact Vishal or Pranav for the credentials if you do not have access to all the services, or are encountering issues with the variables.* 
- Run: `yarn gen` to generate all the types from - `schema.prisma`
- Run: `yarn dev` to spawn a server. The server will automatically restart when you make changes. Note that sometimes you'll have to rerun the script to make sure all changes get reflected.
- Navigate to `http://localhost:5000/` and play with the GraphQL API in the Apollo playground. This is where you can access the documentation as well. 
- Run `npx prisma studio` to visualize the database and make changes to it. 

#### 1.3 Making changes to the database schema
- Whenever changes are made to the prisma schema entities, i.e, the `schema.prisma`  run `yarn gen` and `npx prisma db push`. You may need to restart the VS Code Extension Host as well. PlanetScale and Prisma automatically and implicitly handle all the database migrations. 


