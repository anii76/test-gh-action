# Simple Hello Action

A simple GitHub Action that greets someone and outputs the current time.

## Usage

### Basic Usage

```yaml
uses: anii76/test-gh-action@v1
with:
  who-to-greet: 'World'
```

### Complete Example

```yaml
name: Greet Someone
on: [push]

jobs:
  hello_world_job:
    runs-on: ubuntu-latest
    name: A job to say hello
    steps:
      - name: Hello world action step
        id: hello
        uses: anii76/test-gh-action@v1
        with:
          who-to-greet: 'Mona the Octocat'
      - name: Get the output time
        run: echo "The time was ${{ steps.hello.outputs.time }}"
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `who-to-greet` | Who to greet | true | `World` |

## Outputs

| Output | Description |
|--------|-------------|
| `time` | The time when the greeting was made |

## Releasing

To create a new release:

1. Update version in `package.json`
2. Run `npm run build` to update the dist folder
3. Commit changes
4. Create and push a new tag: `git tag -a v1.0.0 -m "Release v1.0.0" && git push origin v1.0.0`
5. Create a GitHub release from the tag
