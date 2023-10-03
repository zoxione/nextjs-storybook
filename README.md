### Commands for installing dependencies
```bash
npx create-next-app@13.4.13
npx storybook init
```

### Workflow file for deployment on chromatic
```yml
# Workflow name
name: "Deploy Storybook"

# Event for the workflow
on: push

# List of jobs
jobs:
  chromatic-deployment:
    # Operating System
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v1

      - name: Install dependencies
        run: npm install

      - name: Publish to Chromatic
        uses: chromaui/action@v1
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          # 👇 Chromatic projectToken, refer to the manage page to obtain it.
          projectToken: ${{ secrets.CHROMATIC_PROJECT_TOKEN }}
```
