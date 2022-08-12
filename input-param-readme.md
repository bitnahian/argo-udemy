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

## Depends Logic

|Task Result|Description|
|:----------|----------:|
|.Succeeded | Task Succeeded|
|.Failed    | Task Failed|
|.Errored   | Task Errored|
|.Skipped   | Task Skipped|
|.Daemoned  | Task Daemoned|

### Boolean Operators
- &&
- ||
- !

### Logic
- depends: "task" -> depends: (task.Succeeded || task.Skipped || task.Daemoned )
- depends: task.AnySucceeded (loops)
- depends: task.AllFailed (loops)

### Compatibility with dependencies:
- Dependencies: [taskA, taskB, taskC] -> depends: "taskA && taskB && taskC"
