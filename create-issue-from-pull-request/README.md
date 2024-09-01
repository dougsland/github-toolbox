# Create Issue from Pull Request

This script retrieves unresolved review comments from a GitHub pull request and optionally creates a GitHub issue with those comments.

## Usage

### Basic Usage

Retrieve unresolved review comments from a GitHub pull request:

```bash
./create-issue-from-pull-request "https://github.com/owner/repo/pull/number"
```

### Create a GitHub Issue with Unresolved Comments

To create a GitHub issue from unresolved comments, use the `--create-issue` flag:

```bash
./create-issue-from-pull-request "https://github.com/owner/repo/pull/number" --create-issue --github-token your_token_here
```

### Using Environment Variables for the Token

You can use an environment variable for the GitHub token:

```bash
export GITHUB_TOKEN=your_token_here
./create-issue-from-pull-request "https://github.com/owner/repo/pull/number" --create-issue
```

### Retrieve More Comments

To retrieve more than the default 100 comments per review thread, use the `--comment-limit` parameter:

```bash
./create-issue-from-pull-request "https://github.com/owner/repo/pull/number" --comment-limit 200
```

### How to Create a GitHub Token

To use this script effectively, you need a GitHub personal access token with **at least** read-only permissions (you won't be able to automatic create a new issue but can read unresolved comments from PRs). Here’s a quick guide on how to create one:

1. **Sign in to GitHub**: Go to [github.com](https://github.com) and log in.
2. **Go to Settings**:
   - Click on your profile picture in the top-right corner.
   - Select **Settings** from the dropdown.
3. **Access Developer Settings**:
   - In the left sidebar, scroll down and click **Developer settings**.
4. **Create a New Token**:
   - Click **Personal access tokens**.
   - Select **Tokens (classic)** (or **Fine-grained tokens** if applicable).
   - Click **Generate new token**.
5. **Set Permissions**:
   - Name your token.
   - For read-only access, select minimal scopes like `repo`, `read:org`, and `read:user`.
6. **Generate the Token**:
   - Set an expiration date (recommended).
   - Click **Generate token**.
   - **Copy the token**—you won’t see it again!
7. **Store It Safely**:
   - Save the token in a secure place (e.g., a password manager).

Now you can use this token with the `--github-token` option or by setting it in the `GITHUB_TOKEN` environment variable.

## Requirements

- Python 3.x
- `requests` library

Install the `requests` library if you don't have it:

```bash
pip install requests
```

## Arguments

- `pr_url` (required): The URL of the GitHub pull request.
- `--github-token` (optional): Your GitHub token for authentication. If not provided, the script will use the `GITHUB_TOKEN` environment variable.
- `--create-issue` (optional): Flag to create an issue on GitHub with the unresolved comments. Default is to print the comments.
- `--comment-limit` (optional): Number of comments to retrieve per review thread. Default is 100.

## Example Commands

### Retrieve Unresolved Comments Only

```bash
./create-issue-from-pull-request "https://github.com/owner/repo/pull/number"
```

### Create a GitHub Issue with Unresolved Comments

```bash
./create-issue-from-pull-request "https://github.com/owner/repo/pull/number" --create-issue --github-token your_token_here
```

### Retrieve 200 Comments Per Review Thread

```bash
./create-issue-from-pull-request "https://github.com/owner/repo/pull/number" --comment-limit 200
```

## Notes

- If you do not provide a GitHub token, you may quickly hit API rate limits.
- The default number of comments retrieved per review thread is 100, but this can be adjusted with the `--comment-limit` parameter.

## License

This project is licensed under the Apache License, Version 2.0. See the [LICENSE](LICENSE) file for more details.
