Replace-Matching-Array-YAML Action
----
Replace array values that matching key in YAML


## Usage
### Inputs
- `source-file` : Source data file path (only support JSON)
- `target-file` : Updated target file path (only support YAML)
- `matching-key` : Matching key name to find in each element of array

### Result
Rewritten target file.

## Example
##### Source File (build-result/build_result.json)
```
{
  "name": "sample-app",
  "image": "sample.com/sample-app:v1.0.1",
  "git_sha": "a3fa8e0"
}
```

##### Target File (manifest.yaml)
```
- name: 'sample-app'
  image: 'sample.com/sample-app:v1.0.0'
  namespace: 'development'
- name: 'example'
  image: 'sample.com/example:latest'
  namespace: 'stage'
```

##### Github Action Workflow
```
- name: Update manifest
  uses: bucketplace/replace-matching-array-yaml@0.1.0
  with:
    source-file: 'build-result/build_result.json'
    target-file: './manifest.yaml'
    matching-key: 'name'
```
