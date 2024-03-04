# xử lý 1 request thông thường
>Request -> check authen -> check author -> validation -> process raw request data -> update database -> Response ( json)

-   Check Authen: sử dụng middleware mặc định của Laravel
-   Check Authorization: đơn giản nhất sử dụng [ACL](https://laravel.com/docs/10.x/authorization) mặc định của Laravel 
-   Validation: sử dụng [Form Request](https://laravel.com/docs/10.x/validation#form-request-validation) của Laravel 
-   Process Raw data: tách ra thành các class riêng gọi là services -> nhớ luôn phải tạo interface và inject interface đó vào trong controller nhé
-   Tương tác với database: Sử dụng repository, inject vào service.

```mermaid
classDiagram
Class01 <|-- AveryLongClass : Cool
Class03 *-- Class04
Class05 o-- Class06
Class07 .. Class08
Class09 --> C2 : Where am i?
Class09 --* C3
Class09 --|> Class07
Class07 : equals()
Class07 : Object[] elementData
Class01 : size()
Class01 : int chimp
Class01 : int gorilla
Class08 <--> C2: Cool label
```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI2NDIyNDQ2NiwtOTQ2MzI3NjU0XX0=
-->