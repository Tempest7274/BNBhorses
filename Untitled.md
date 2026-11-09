
# Logical Schema – Hotel App  
  
**PK** = primary key, *FK* = foreign key  
  
## Tables  
  
**Client**(**DNI**, Nombre, Apellidos, telefono)  
- The composite `Nombre` is flattened into `Nombre` and `Apellidos`.  
  
**Hotel**(**id**, Nombre, telefono, estrellas, Direccion, Pais)  
  
**RoomType**(**tipo**, capacidad, descripcion)  
  
**Room**(**id_hotel**, **Numero**, Planta, precio, *tipo*)  
- `id_hotel` → Hotel.id, NOT NULL. Room is a weak entity, so the hotel's key is part of its PK.  
- `tipo` → RoomType.tipo, NOT NULL.  
  
**Reservation**(**id_reservation**, date, number_of_days, *DNI*)  
- `DNI` → Client.DNI, NOT NULL.  
  
**Payment**(**id_payment**, amount, payment_date, payment_method, *id_reservation*)  
- `id_reservation` → Reservation.id_reservation, NOT NULL.  
  
**Reserv_ROOM**(**id_reservation**, **id_hotel**, **Numero**)  
- Associative entity. Its PK is the combination of the keys of the entities it links.  
- `id_reservation` → Reservation.id_reservation.  
- `(id_hotel, Numero)` → Room.(id_hotel, Numero).  
  
## Relationship mapping  
  
| Relationship | Cardinality | Becomes |  
|---|---|---|  
| Hotel *holds* Room | 1 : N, identifying | `id_hotel` in Room's PK |  
| RoomType *type is* Room | 1 : N | `tipo` FK in Room |  
| Client *makes* Reservation | 1 : N | `DNI` FK in Reservation |  
| Reservation *receives* Payment | 1 : N | `id_reservation` FK in Payment |  
| Reservation *contains* Reserv_ROOM | 1 : N | FK in Reserv_ROOM |  
| Reserv_ROOM *included in* Room | N : 1 | FK in Reserv_ROOM |  
  
## Notes  
- `date` is a reserved word in most DBMSs.  
- `number_of_days` needs underscores because the diagram's version has spaces.