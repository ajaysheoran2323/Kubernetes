## Question 1

1. Create a namespace called `ggckad-s0` in your cluster.
2. Run the following pods in this namespace:

      A pod called `pod-a` with a single container running the `kubegoldenguide/simple-http-server` image
      A pod called `pod-b` that has one container running the `kubegoldenguide/alpine-spin:1.0.0` image, and one container running `nginx:1.7.9`


Write down the output of `kubectl get pods` for the `ggckad-s0` namespace and put in Issues section.
