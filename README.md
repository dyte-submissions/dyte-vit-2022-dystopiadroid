
# Dyte-Task (pkg-version-tracer)

CLI tool to verify/update the current version of a dependency used in a public/private github repository mentioned in a CSV file


## Basic Usage

To compare the version of dependency in the repository with respect to the specified dependency in the argument. 

```bash
  npx pkg-version-tracker -i <CSV-file> <dep@version>
```

To generate pull request for the repositories whose dependency have lower version with respect to the dependency in the argument. 

```bash
  npx pkg-version-tracker -update -i <CSV-file> <dep@version>
```
    
## Github APIs used

#### Create a fork

```
  POST repos/{owner}/{repo}/forks
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `owner` | `string` | **Required**. Account owner of repository |
| `repo` | `string` | **Required**. Name of the repository |


#### Get Branches

```
  GET /repos/{owner}/{repo}/branches
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `owner` | `string` | **Required**. Account owner of repository |
| `repo` | `string` | **Required**. Name of the repository |


#### Create a new branch

```
  POST /repos/{owner}/{repo}/git/refs
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `owner` | `string` | **Required**. Account owner of repository |
| `repo` | `string` | **Required**. Name of the repository |
| `ref` | `string` | **Required**. Name of fully qualified reference ( ref/heads/featureA )
| `sha` | `string` | **Required**. The SHA1 value for this reference |

#### Get content from repository

```
  GET /repos/{owner}/{repo}/contents/{path}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `owner` | `string` | **Required**. Account owner of repository |
| `repo` | `string` | **Required**. Name of the repository |
| `path` | `string` | **Required**. Path parameter |

#### Update content from repository

```
  PUT /repos/{owner}/{repo}/contents/{path}
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `owner` | `string` | **Required**. Account owner of repository |
| `repo` | `string` | **Required**. Name of the repository |
| `path` | `string` | **Required**. Path parameter |
| `message` | `string` | **Required**. Commit message |
| `committer.name` | `string` | **Required**. Name of the author or committer |
| `committer.email` | `string` | **Required**. Email of the author or committer |
| `content` | `string` | **Required**. THe new files content (base64 encoded) |

#### Create pull request

```
  POST /repos/{owner}/{repo}/pulls
```

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `owner` | `string` | **Required**. Account owner of repository |
| `repo` | `string` | **Required**. Name of the repository |
| `title` | `string` | **Required**. The title of new pull request |
| `body` | `string` | **Required**. Contents of the pull request|
| `head` | `string` | **Required**. The name of the branch where your changes are implemented |
| `base` | `string` | **Required**. The name of the branch you want the changes pulled into |







