# GitHubActions

![](https://github.com/Saphall/GitHubActions/workflows/Python%20application/badge.svg)

Creating a simple CI/CD Pipeline using GitHub Actions for Python Project using GitHub Actions.

> Actions are individual tasks that we can combine to create jobs and customize our workflow. We can create our own actions, and use and customize actions shared by the GitHub community. Refer : [https://github.com/features/actions](https://github.com/features/actions)

<img src='https://journeyofquality.files.wordpress.com/2020/11/cicd-tools.jpg' width=50% alt=' CI/CD IMAGE'>

## Continuous Integration

<details open>
 <summary> Details: </summary>
Continuous integration (CI) is a software practice that requires frequently committing code to a shared repository.

When we commit code to our repository, we can continuously build and test the code to make sure that the commit doesn't introduce errors. Our tests can include code linters (which check style formatting), security checks, code coverage, functional tests, and other custom checks.

Building and testing our code requires a server. We can build and test updates locally before pushing code to a repository, or we can use a CI server that checks for new code commits in a repository.

> GitHub offers CI workflow templates for a variety of languages and frameworks.
> Browse the complete list of CI workflow templates offered by GitHub in the [actions/starter-workflows](https://github.com/actions/starter-workflows/tree/master/ci) repository.

</details>

## Continuous Deployment

<details open>
  <summary> Details: </summary>
  Continuous deployment is a strategy for software releases wherein any code commit that passes the automated testing phase is automatically released into the production environment, making changes that are visible to the software's users.
  </details>

## Deploying Python Application on Heroku

- Install [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
- Login to Heroku CLI session: heroku login
- Create new Heroku App: heroku create
- [Generate Authentication Token](https://devcenter.heroku.com/articles/platform-api-quickstart#authentication): heroku authorizations:create
- 'Deploy to Heroku' Action:

```yml
yml
- name: Deploy to Heroku
  env:
    HEROKU_API_TOKEN: ${{ secrets.HEROKU_API_TOKEN }}
    HEROKU_APP_NAME: ${{ secrets.HEROKU_APP_NAME }}
  if: github.ref == 'refs/heads/master' && job.status == 'success'
  run: |
    git remote add heroku https://heroku:$HEROKU_API_TOKEN@git.heroku.com/$HEROKU_APP_NAME.git
    git push heroku HEAD:master -f
```

## References

1. https://www.youtube.com/watch?v=WTofttoD2xg
2. https://help.github.com/en/actions/reference/workflow-syntax-for-github-actions
