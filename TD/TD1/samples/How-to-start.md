# Set up our Kafka cluster on the cloud 
### Disclaimer: 

__As part of your Confluent Cloud trial, you are provided with 400\$ in credits for use during the 30-day trial period.__ 
__Please note that it is your responsibility to manage your account and monitor your usage. Any additional charges incurred beyond the 400\$ credit or after the trial period ends will be your sole responsibility. Be sure to track your credit usage and the trial period's expiration to avoid any unexpected costs.__

__Please keep your eyes on [Billing & Payment](#monitoring-billing-and-payment) section to keep track of the credit and the spends__

## Sign-up for Confluent Cloud

- Start here at Confluent.io: https://www.confluent.io/get-started/

- Choose you deployment: `CLOUD`
- Sign up by filling in form with your: 
  + Full Name
  + Company
  + Email 
- Click on `Start Free`

💡 Keep in mind the [Disclaimer](#disclaimer) of the trial period. 

## Getting started 
### 💻 Configuring your cluster

- Choose the type of cluster as follow: 
<image>

- Enter your payment info. Please consider the [Disclaimer](#disclaimer) of the trial period. 

### 🖥️ Configuring your client
#### 1. Create an API Key:
- Create an API key. 
- Save the key somewhere for safety.

#### 2. Create your topic
You can follow the tutorial of Confluent page, where you can copy the code with the variables already filled. Otherwise, you can take a look hereunder.

Using the following command in your terminal, and replace the following placeholders:
- `<name_of_topic_to_replace>`: replace with your topic name
- `<your-server-address>`: in your cluster details
- `<base64-encoded-API-key-and-secret>`: base64-encoded API key and secret in the following format `<key>:<secret>`
```
curl \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Basic <base64-encoded-API-key-and-secret>" \
  https://<your-server-address>:443/kafka/v3/clusters/lkc-npk70k/topics \
  -d '{"topic_name":"<name_of_topic_to_replace>"}'
```

Once this command is run successfully, your new topic will be displayed in the Confluent console (not in the tutorial page).

You can also copy the details for configuration on client-side for later use: 

```
# Required connection configs for Kafka producer, consumer, and admin
bootstrap.servers=<your-server-address>:9092
security.protocol=SASL_SSL
sasl.mechanisms=PLAIN
sasl.username={{ CLUSTER_API_KEY }}
sasl.password={{ CLUSTER_API_SECRET }}

# Best practice for higher availability in librdkafka clients prior to 1.7
session.timeout.ms=45000

```

## 💰 Monitoring Billing and Payment
Your Billing and Payment section: https://confluent.cloud/settings/billing/invoice