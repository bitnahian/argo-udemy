## Run argo workflow

```sh
argo -n argo submit wf-input-parameter-dag.yaml
```

## Delete workflow in Argo
Cannot run the same workflow if it already exists in argo

```sh
argo -n argo delete wf-input-parameter-dag-template
```

## List workflows

```sh
argo -n argo list
```

## Terminal Parameter Override

```sh
argo -n argo submit wf-input-parameter-dag.yaml -p message1="Param used from terminal"
```

## Use parameter file

```sh
argo -n argo submit wf-input-parameter-dag.yaml --parameter-file input-dag-parameters.yaml
```