
# Overview

This is the repository that contains the DRY (Don't Repeat Yourself) manifests for application "acm".

# File Structure

This application was bootstrapped using the `kustomize` format, which follows the following structure:
```
|-config/
  |-base/
    |-kustomization.yaml
  |-envs/
|-delivery/
  |-envs/
|-validation/
  |-resources/
  |-functions/
    |-kubeval-validator.yaml
|-.appctlconfig
|-.deployment
```
- `config/`: the top-level directory of the DRY manifests.
  - `base/`: **(Optional)** the [base](https://kubernetes-sigs.github.io/kustomize/api-reference/glossary/#base) directory that kustomizations refer to.
    - `kustomization.yaml`: **(Optional)** a [kustomization](https://kubernetes-sigs.github.io/kustomize/api-reference/glossary/#kustomization) file contains resources, generators, transformers or metadata.
  - `envs/`: the environment [overlays](https://kubernetes-sigs.github.io/kustomize/api-reference/glossary/#overlay).
- `delivery/envs/`: the directory of the environment-related configurations.
- `validation/`: the top-level directory of the validation-related configurations. `appctl` is using `kpt fn` to declaratively validate the hydrated manifests.
  - `resources/`: the directory to hold additional validation resources, such as constraints.
  - `functions/`: the directory to hold multiple validation configurations. Please check the list of existing [Kpt validators](https://googlecontainertools.github.io/kpt/guides/consumer/function/catalog/validators/).
    - `kubeval-validator.yaml`: the default validator.
- `.appctlconfig`: a hidden file has the application-level configurations.
- `.deployment`: a directory of the local copy of the deployment repository.
