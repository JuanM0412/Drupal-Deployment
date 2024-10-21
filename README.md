<div align="center">

# Drupal Deployment

</div>

### ST0263-242 Tópicos Especiales en Telemática

### Students:
- Juan Manuel Gómez P. (jmgomezp@eafit.edu.co)
- Miguel Ángel Hoyos V. (mahoyosv@eafit.edu.co)
- Santiago Neusa R. (sneusar@eafit.edu.co)
- Sebastian Restrepo O. (srestrep74@eafit.edu.co)
- Luisa Maria Alvarez G. (lmalvarez8@eafit.edu.co)

### Professor:
- Edwin Nelson Montoya M. (emontoya@eafit.edu.co)

## 1. Deploying Drupal on EKS cluster

First, you need to create an EKS cluster on AWS and an EFS file system. Access the EKS cluster through CloudShell to make it easy to connect and execute all commands.

### 3.1. Generate and prepare the manifests

1. Clone the repository:
    ```
    git clone https://github.com/JuanM0412/Drupal-Deployment.git
    ```

2. Access the directory created as a result of the previous step:
    ```
    cd Drupal-Deployment
    ```

3. Run the following command to install the Amazon EFS CSI driver:
    ```
    kubectl apply -k "github.com/kubernetes-sigs/aws-efs-csi-driver/deploy/kubernetes/overlays/stable/ecr/?ref=release-1.5"
    ```

4. Modify the volumeHandle in the `drupal-deployment.yaml` file according to the ID of your EFS.

5. Execute the manifests:
    ```
    kubectl apply -k .
    ```

6. Check the status of the pods:
    ```
    kubectl get pods
    ```

7. When the pods are running execute:
    ```
    kubectl get all
    ```

8. You will see the DNS (external IP) for the Load Balancer, copy and paste that address into your browser and you should see the Drupal installation page.