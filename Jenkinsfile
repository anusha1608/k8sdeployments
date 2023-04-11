pipeline {
    agent {
        node {
            label 'java11'
        }
    }
    options {
        timestamps()
        buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '2'))
        timeout(time: 240, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    stages {
        stage ('K8SManifest-Checkout') {
            steps {
                git 'https://github.com/anusha1608/k8sdeployments.git'
            }
        }
        stage ('Kubernetes AutoDeployment') {
            steps {
                dir('manifests')
                {
                    sh 'ls -l'
                    sh 'kubectl --server=https://34.28.87.115 --insecure-skip-tls-verify --token="eyJhbGciOiJSUzI1NiIsImtpZCI6Ilp4cHNNbTl3MmQ2N0hCNWlxeEkzSmVrLU5pTzJFNkJac0tDX3NYS1RBSFUifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImplbmtpbnMtc2EiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoiamVua2lucyIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6ImNjMzViNGYwLWM5MWMtNGUxZS1hNDI3LWUxNzFmMDM0OTM4YyIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDpkZWZhdWx0OmplbmtpbnMifQ.YOk9TQEdrKX2NMCLFN62SKlB6lRmtEQo-XM-dw5lOeMdEJDDcBiZ5BhDGJWs5mHCZpXUEWvj1QaF5TAwlbgkZRWtwCPpB9tfe1_N5wll3_oua6JV9wbeAFuUO_YBxCq9nA2CxI5ZtA_YvkxqwdCcNfpjee1f-dlCf-Q2mS3DJ4GBZYnEwVUsVYTUlebww5Yyuv2ofFmDVNgvANziTOM2pey4hsXFt0F5FEO-ifOhtfCR3LLNxazN6y5724IHo2ap9E8XkD3WoMZOfLpwDxRo4Wz_sF7vX2lOpHeT10U74nivjR6A-cd_o9wEsze81VeO7BE3kCSNnajPCB6cR1AYrA" apply -f deployment.yml'
                    sh 'kubectl --server=https://34.28.87.115 --insecure-skip-tls-verify --token="eyJhbGciOiJSUzI1NiIsImtpZCI6Ilp4cHNNbTl3MmQ2N0hCNWlxeEkzSmVrLU5pTzJFNkJac0tDX3NYS1RBSFUifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImplbmtpbnMtc2EiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoiamVua2lucyIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6ImNjMzViNGYwLWM5MWMtNGUxZS1hNDI3LWUxNzFmMDM0OTM4YyIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDpkZWZhdWx0OmplbmtpbnMifQ.YOk9TQEdrKX2NMCLFN62SKlB6lRmtEQo-XM-dw5lOeMdEJDDcBiZ5BhDGJWs5mHCZpXUEWvj1QaF5TAwlbgkZRWtwCPpB9tfe1_N5wll3_oua6JV9wbeAFuUO_YBxCq9nA2CxI5ZtA_YvkxqwdCcNfpjee1f-dlCf-Q2mS3DJ4GBZYnEwVUsVYTUlebww5Yyuv2ofFmDVNgvANziTOM2pey4hsXFt0F5FEO-ifOhtfCR3LLNxazN6y5724IHo2ap9E8XkD3WoMZOfLpwDxRo4Wz_sF7vX2lOpHeT10U74nivjR6A-cd_o9wEsze81VeO7BE3kCSNnajPCB6cR1AYrA" apply -f service.yml'
                    echo 'Done'
                    sh 'kubectl get deployments'
                    sh 'sleep 60; kubectl get services'
                    cleanWs()
                }
            }
        }
    }
}