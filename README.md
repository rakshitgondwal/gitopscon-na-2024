# Demo for GitOpsCon North America 2024

## Talk: Don't GitOps into a Blackhole

## Follow along:

- **Install the Keptn Lifecycle Toolkit**

    ```
    helm repo add keptn https://charts.lifecycle.keptn.sh
    helm repo update
    helm upgrade --install keptn keptn/keptn -n keptn-system --create-namespace --wait
    ```

- **Setup Prometheus on your cluster**
    You can setup prometheus from both `lifecycle/` or `metrics/`. `cd` into any one of these and do a
    ```
    make install
    ```

## For lifecycle part:
...

## For metrics part:

- **Deploy the Demo application**  
    This would deploy a `Deployment` and a `Service` on you Cluster.
    ```
    kubectl apply -f deployment.yaml
    ```
    Wait for the workload to be ready, you can see the status using `kubectl get all -n podtato-kubectl`

- **Deploy the `KeptnMetricsProivder`**
    ```
    kubectl apply -f metricprovider.yaml
    ```

- **Deploy the `KeptnMetric`**
    ```
    kubectl apply -f keptnmetric.yaml
    ```
- Now you can check the metric value for you application using
    ```
    kubectl get KeptnMetric -n podtato-kubectl
    ```
  Check the no. of pods running for your application using `kubectl get pods -n podtato-kubectl `, should be 1.

- **Apply `HorizontalPodAutoscaler`**
    ```
    kubectl apply -f hpa.yaml
    ```

- Check for the no. of pods for your application again, should be 3 now, if no, wait for some time, the pods will start getting created in some time.
