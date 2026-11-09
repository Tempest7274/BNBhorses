**PK** = primary key, *FK* = foreign key, */attr* = derived attribute (not stored)

## Tables

**client**(**nationalId**, firstName, lastName, phone)
- The composite `name` is flattened into `firstName` and `lastName`.

**hotel**(**hotelId**, name, phone, stars, address, country)

**roomType**(**typeName**, capacity, description)

**room**(**hotelId**, **roomNumber**, floor, price, *typeName*)
- `hotelId` → hotel.hotelId, NOT NULL. Room is a weak entity, so the hotel's key is part of its PK.
- `typeName` → roomType.typeName, NOT NULL.

**reservation**(**reservationId**, bookingDate, checkInDate, checkOutDate, */numberOfDays*, *nationalId*)
- `/numberOfDays` is derived: `checkOutDate - checkInDate`.
- `nationalId` → client.nationalId, NOT NULL.

**payment**(**paymentId**, amount, paymentDate, paymentMethod, *reservationId*)
- `reservationId` → reservation.reservationId, NOT NULL.

**reservationRoom**(**reservationId**, **hotelId**, **roomNumber**)
- Associative entity. Its PK is the combination of the keys of the entities it links.
- `reservationId` → reservation.reservationId.
- `(hotelId, roomNumber)` → room.(hotelId, roomNumber).

## Relationship mapping

| Relationship                           | Cardinality        | Becomes                        |
| -------------------------------------- | ------------------ | ------------------------------ |
| hotel *holds* room                     | 1 : N, identifying | `hotelId` in room's PK         |
| roomType *hasType* room                | 1 : N              | `typeName` FK in room          |
| client *makes* reservation             | 1 : N              | `nationalId` FK in reservation |
| reservation *receives* payment         | 1 : N              | `reservationId` FK in payment  |
| reservation *contains* reservationRoom | 1 : N              | FK in reservationRoom          |
| reservationRoom *includedIn* room      | N : 1              | FK in reservationRoom          |

## Notes
- `checkOutDate` must be after `checkInDate`.
- `numberOfDays` is not stored; compute it in queries from the two dates.