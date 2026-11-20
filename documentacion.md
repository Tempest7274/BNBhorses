En nuestro proyecto vamos a partir de una agencia de hoteles, queremos ayudar a que los clientes puedan recibir el mejor trato posible y la mayor comodidad posible

  

qué información necesitamos guardar

  
el modelo de negocio es este

  

un hotel puede tener varias habitaciones

un usuario busca un hotel y hace una reserva

paga por la reserva

  
  
  
  
  

el usuario puede hacer una reserva, indicando la fecha los dias etc, selecionar el tipo de habitación: single, double, o suit, y realizar el pago

Reserva, el usuario reserva la habitacion en nuestro hotel mediante la aplicacion y realiza un pago

  
  

entidades: 

- cliente—> DNI(PK),nombre,apellidos,telefono
    
- hotel—-->id_hotel (PK)nombre, estrellas, telefono, direccion, ciudad,pais ( pon atributo multivalorado)
    
- habitacion—-> id_habitacion(PK)numero,planta
    
- tipo de habitación, id_tipo(PK)nombre(single/double/suite),capacidad,precio
    
- reserva, id_reserva(PK)fecha_entrada,fecha_salida, num_personas
    
- pago, id_pago(PK)fecha_pago,metodo(efectivo,tarjeta),,estado
    

algunos atributos podemos poner finalmente relacion y si tienen el mismo atributo le hacemos relación con atributo