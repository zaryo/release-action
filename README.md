# release-action

Github action to be used in workflows. Contains the following action:

`match-version`: Asserts the project version against the pushed tag version, it accepts one required input: 
- `source`: The source from where the single-source-of-truth version will come from. It currently supports two options; `binary` and `browser_extension_manifest`. `binary` will require a second input `filename`, it will run `filename --version` and compare it with the pushed tag version. Similarly, `browser_extension_manifest` will look for `manifest.json` in the root of the project, it expects it to be a browser extension manifest, and will get the value of `version` field. 

### Usage in a workflow:

```yml
- uses: zaryo/release-action/match-version@76ef078d42167af71c4a33c0d0383279c8a71475
  with:
    source: binary
    filename: <binary_path>
```

```yml
- uses: zaryo/release-action/match-version@76ef078d42167af71c4a33c0d0383279c8a71475
  with:
    source: browser_extension_manifest
```
