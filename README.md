# start-opensearch
Github action to start an OpenSearch instance 

```yaml
inputs:
  opensearch-version:
    description: 'The version of OpenSearch that should be used, e.g "3.0.0"'
    required: true

  plugins:
    description: 'A comma separated list of plugins to install. Leave empty to not install any. Each entry should be a full path prefixed with `file: `, for example: `file:$(pwd)/my-plugin.zip`'
    required: false

  security-enabled:
    description: 'Whether security is enabled'
    required: true

  admin-password:
    description: 'The admin password uses for the cluster'
    required: false

  security_config_file:
    description: 'Path to a security config file to replace the default. Leave empty if security is not enabled or using the default config'
    required: false
```

## Usage:

```yaml
steps:
- name: Run Opensearch with A Single Plugin
  uses: derek-ho/start-opensearch@v1
  with:
    opensearch-version: ${{ env.OPENSEARCH_VERSION }}
    plugins: "file:${{ github.workspace }}/${{ env.PLUGIN_NAME }}.zip"
    security-enabled: true
    admin-password: ${{ steps.random-password.outputs.generated_name }}
```

# Changelog

## v1
- Initial Release