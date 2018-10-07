# Alpine Elixir Release (AER)

Imagine if everything was built on AER.

Based on https://github.com/bitwalker/distillery/blob/2.0.10/docs/guides/working_with_docker.md#the-dockerfile

## Usage

Copy the Dockerfile into your project's root.

When building the image, provide the following build args:

- `APP_NAME` - the name of your application/release
- `APP_VSN` - the version of the application we are building (required)
- `MIX_ENV` - the environment to build with
- `SKIP_PHOENIX` - set this to true if this release is not a Phoenix app

If you are using an umbrella project, you can change this argument to the
directory of the Phoenix app so that the assets can be built:

- `PHOENIX_SUBDIR`

Example build and run commands:

```
docker build \
  --build-arg APP_NAME=$(APP_NAME) \
  --build-arg APP_VSN=$(APP_VSN) \
  -t $(APP_NAME):$(APP_VSN)-$(BUILD) \
  -t $(APP_NAME):latest .

docker run \
  --expose 4000 -p 4000:4000 \
  --rm -it $(APP_NAME):latest
```
