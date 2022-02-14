# k8s-wait-for

**From: https://github.com/groundnuty/k8s-wait-for**

A simple script that allows waiting for a k8s service, job or pods to enter the
desired state.

## Running

You can start simple. Run it on your cluster in a namespace you already have
something deployed:

```bash
kubectl run --generator=run-pod/v1 k8s-wait-for --rm -it --image groundnuty/k8s-wait-for:v1.3 --restart Never --command /bin/sh
```

Read `--help` and play with it!

```bash
/ > wait_for.sh -h
This script waits until a job, pod or service enter a ready state.

wait_for.sh job [<job name> | -l<kubectl selector>]
wait_for.sh pod [<pod name> | -l<kubectl selector>]
wait_for.sh service [<service name> | -l<kubectl selector>]

Examples:
Wait for all pods with a following label to enter 'Ready' state:
wait_for.sh pod -lapp=develop-volume-gluster-krakow

Wait for all pods with a following label to enter 'Ready' or 'Error' state:
wait_for.sh pod-we -lapp=develop-volume-gluster-krakow

Wait for all the pods in that job to have a 'Succeeded' state:
wait_for.sh job develop-volume-s3-krakow-init

Wait for all the pods in that job to have a 'Succeeded' or 'Failed' state:
wait_for.sh job-we develop-volume-s3-krakow-init

Wait for at least one pod in that job to have 'Succeeded' state, does not mind some 'Failed' ones:
${0##*/} job-wr develop-volume-s3-krakow-init

Wait for all selected pods to enter the 'Ready' state:
wait_for.sh pod -l"release in (develop), chart notin (cross-support-job-3p)"
```
