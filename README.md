# Microservice


## Architecture

**Online Boutique** is composed of 11 microservices written in different
languages that talk to each other over gRPC.

### Architecture of microservices
<img width="1778" alt="architecture-diagram" src="https://github.com/user-attachments/assets/679f68e9-a3c2-46b2-8ce2-2eb672318eaf">


| Service                                              | Language      | Description                                                                                                                       |
| ---------------------------------------------------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [frontend](https://github.com/Pramod858/Microservice/tree/frontend)                           | Go            | Exposes an HTTP server to serve the website. Does not require signup/login and generates session IDs for all users automatically. |
| [cartservice](https://github.com/Pramod858/Microservice/tree/cartservice)                     | C#            | Stores the items in the user's shopping cart in Redis and retrieves it.                                                           |
| [productcatalogservice](https://github.com/Pramod858/Microservice/tree/productcatalogservice) | Go            | Provides the list of products from a JSON file and ability to search products and get individual products.                        |
| [currencyservice](https://github.com/Pramod858/Microservice/tree/currencyservice)             | Node.js       | Converts one money amount to another currency. Uses real values fetched from European Central Bank. It's the highest QPS service. |
| [paymentservice](https://github.com/Pramod858/Microservice/tree/paymentservice)               | Node.js       | Charges the given credit card info (mock) with the given amount and returns a transaction ID.                                     |
| [shippingservice](https://github.com/Pramod858/Microservice/tree/shippingservice)             | Go            | Gives shipping cost estimates based on the shopping cart. Ships items to the given address (mock)                                 |
| [emailservice](https://github.com/Pramod858/Microservice/tree/emailservice)                   | Python        | Sends users an order confirmation email (mock).                                                                                   |
| [checkoutservice](https://github.com/Pramod858/Microservice/tree/checkoutservice)             | Go            | Retrieves user cart, prepares order and orchestrates the payment, shipping and the email notification.                            |
| [recommendationservice](https://github.com/Pramod858/Microservice/tree/recommendationservice) | Python        | Recommends other products based on what's given in the cart.                                                                      |
| [adservice](https://github.com/Pramod858/Microservice/tree/adservice)                         | Java          | Provides text ads based on given context words.                                                                                   |
| [loadgenerator](https://github.com/Pramod858/Microservice/tree/adservice/loadgenerator)                 | Python/Locust | Continuously sends requests imitating realistic user shopping flows to the frontend.                                              |

## Screenshots

| Home Page                                                                                                         | Checkout Screen                                                                                                    |
| ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| [![Screenshot of store homepage](https://github.com/user-attachments/assets/9afe43bb-5883-4000-9b4e-9fa5cb3a9c38)](https://github.com/user-attachments/assets/9afe43bb-5883-4000-9b4e-9fa5cb3a9c38) | [![Screenshot of checkout screen](https://github.com/user-attachments/assets/324cd36d-b1ac-4657-94ec-90bb457c042c)](https://github.com/user-attachments/assets/324cd36d-b1ac-4657-94ec-90bb457c042c) | 

#### Multibranch Pipeline (Jenkins)
![Multibranch Pipeline (Jenkins)](https://github.com/user-attachments/assets/a01abd40-780f-4bc1-a231-4bdcea93170b)


### ![For Complete Source Code Click Here](https://github.com/GoogleCloudPlatform/microservices-demo)
