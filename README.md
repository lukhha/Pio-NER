
# Pio-NER

This is a proposal walkthrough. For notebook walk through please open main_notebook.ipynb

Publicis sapient Input-to-Ouput Named Entity Recognition is a platform that will help our customers to extract insights from Natural Language. 

While the name has Named Entity Recognition in it, it is well versed with multiple tasks such as: 
1. Text2SQL
2. POS tagging
3. NER tagging 
4. Ticketing Agent and much more!

We will today dive into NER tagging functionality of the same. 

1. Read the sentences from OLAP (postgres) & OLTP (data-lake) database. 
2. Run them through inference pipeline. 
3. Store the results back in the database


NER Architecture


```mermaid
graph TD;
    A["MLflow remote server"] --> B["Data Scientist local system"];
    B --> A;
    A --> C["Amazon S3, ECR, EKS, EC2"];
    A --> D["GitHub runner (CI/CD)"];
    D --> A;
    C --> D;
    D --> C;
```

```mermaid
block-beta
    columns 3
    doc>"Data Scientist Local"]:3
    space down1<[" "]>(updown) space

  block:e:3
          l["Github Runner (CICD)"]
          m("MLflow Server")
          r["Github"]         
  end

    space updown <[" "]>(updown) space
    aws["AWS"]:3
    db[("AWS POSTGRES")]:2
    space:3
    EC2,ECR,EKS space S3bucket
    aws <--> EC2,ECR,EKS
    S3bucket <--> aws
    EC2,ECR,EKS <--> S3bucket
    EC2,ECR,EKS <--> db
    DASH <--> db

    style m fill:#d6d,stroke:#333,stroke-width:4px

```





