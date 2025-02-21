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


 
