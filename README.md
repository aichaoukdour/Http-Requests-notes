# What is HTTP?
HTTP stands for Hypertext Transfer Protocol and is used to structure requests and responses over the internet. HTTP requires data to be transferred from one point to another over the network.
The transfer of resources happens using TCP (Transmission Control Protocol). In viewing this webpage, TCP manages the channels between your browser and the server (in this case, github.com). TCP is used to manage many types of internet connections in which one computer or device wants to send something to another. HTTP is the command language that the devices on both sides of the connection must follow in order to communicate.

<img width="284" alt="image" src="https://github.com/user-attachments/assets/802f5be9-2eed-4796-b853-1e9e7ddfe019" />


---

## Http methodes

![image](https://github.com/user-attachments/assets/7f7e71c1-6a24-444f-a8d9-4a05b3813c15)

1. HTTP GET 
This retrieves a resource from the server. It is idempotent. Multiple identical requests return the same result. 
 
2. HTTP PUT 
This updates or Creates a resource. It is idempotent. Multiple identical requests will update the same resource. 
 
3. HTTP POST 
This is used to create new resources. It is not idempotent, making two identical POST will duplicate the resource creation. 
 
4. HTTP DELETE 
This is used to delete a resource. It is idempotent. Multiple identical requests will delete the same resource. 
 
5. HTTP PATCH 
The PATCH method applies partial modifications to a resource. 
 
6. HTTP HEAD 
The HEAD method asks for a response identical to a GET request but without the response body. 
 
7. HTTP CONNECT 
The CONNECT method establishes a tunnel to the server identified by the target resource. 
 
8. HTTP OPTIONS 
This describes the communication options for the target resource. 
 
9. HTTP TRACE 
This performs a message loop-back test along the path to the target resource.

---

## Status

![image](https://github.com/user-attachments/assets/5704d709-c3bf-4f99-9e6e-f2151f47fcb3)

---

# Mécanisme des Requêtes HTTP entre Deux Tiers et Plus

## 1. Communication Client-Serveur (2 Tiers)
Le modèle le plus simple où un client (navigateur ou application) envoie une requête HTTP à un serveur, et ce dernier renvoie une réponse.

### **Processus :**
- Le client envoie une requête HTTP (GET, POST, etc.) vers le serveur.
- Le serveur traite la requête (lecture d’une base de données, exécution d’une logique métier, etc.).
- Le serveur renvoie une réponse HTTP avec un code de statut (200 OK, 404 Not Found, etc.).

#### **Exemple d’échange entre un navigateur et un serveur**  
```
Client → HTTP Request (GET /products) → Serveur  
Serveur → HTTP Response (200 OK, JSON des produits) → Client  
```

---

## 2. Architecture à 3 Tiers (Client-Serveur-Base de Données ou API Gateway)
Dans ce cas, un serveur intermédiaire (back-end) communique avec une base de données ou un autre serveur via HTTP.

### **Processus :**
- Le client envoie une requête au serveur d’application (backend).
- Le backend fait une autre requête HTTP vers un serveur tiers (ex : microservice, API externe).
- Le serveur tiers renvoie une réponse au backend.
- Le backend reformate et renvoie la réponse au client.

#### **Exemple avec un backend qui interroge une base de données via une API interne**  
```
Client → HTTP Request (GET /products) → Backend  
Backend → HTTP Request (GET /db/products) → Serveur de base de données  
Serveur DB → HTTP Response (200 OK, données produits) → Backend  
Backend → HTTP Response (200 OK, JSON produits) → Client  
```

---

## 3. Communication entre Plusieurs Microservices (N-Tiers)
Dans une architecture distribuée (microservices), plusieurs services communiquent entre eux via HTTP, généralement via un **API Gateway** ou un **Service Mesh**.

### **Processus avec un API Gateway :**
- Le client envoie une requête HTTP à un API Gateway.
- L’API Gateway répartit les requêtes vers différents microservices (produits, panier, paiement, etc.).
- Chaque microservice peut interagir avec d’autres services (ex : service de paiement contacte la banque).
- La réponse agrégée est renvoyée au client.

#### **Exemple avec microservices**  
```
Client → HTTP Request (POST /checkout) → API Gateway  
API Gateway → HTTP Request (GET /cart) → Cart Service  
API Gateway → HTTP Request (GET /payment) → Payment Service  
API Gateway → HTTP Response (200 OK, commande validée) → Client  
```

### **Technologies Utilisées dans les Architectures Multi-Tiers :**
- **API Gateway** (ex : Kong, Zuul, Spring Cloud Gateway) pour gérer les routes et sécuriser les requêtes.
- **Service Mesh** (ex : Istio, Linkerd) pour gérer la communication interservices.
- **Message Broker** (ex : Kafka, RabbitMQ) pour des communications asynchrones entre services.

---

## **Conclusion**
- **2 Tiers** : Client ↔ Serveur  
- **3 Tiers** : Client ↔ Backend ↔ Base de données / API  
- **N-Tiers (Microservices)** : Client ↔ API Gateway ↔ Microservices ↔ Autres Services  

---


 
