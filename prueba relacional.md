 **Empresa y coche de empresa:

  
  

DEPARTAMENTO(#cod_depto, nombre, planta)

  

EMPLEADO(#DNI, nombre, salario, cod_depto NN, fecha incorporación,DNI_JEFENN)

  

OP.BORRADO(cod_depto) -RESTRICT

OP.BORRADO(DNI_jefe)- SET NULL

  
  

COCHE(#matricula, marca,modelo)

  

EMPLEADO_COCHE(#DNI,matriculaUNIQUE,NOTNULL)

  

OP.BORRADO(DNI) -CASCADE

OP.BORRADO(matrícula)- CASCADE

  

Red social:

  

USUARIO(#nick,email,fecha_alta)

  

PUBLICACION(#id_publicacion,fecha,texto,nicknn

  

OP.BORRADO(cod_usuario) -Cascade

  

LIKES(#(nick, id_publicacion),fecha)

  

op.borrado(nick) - CASCADE

op.borrado(id.publicacion) -CASCADE

  

SEGUIDORES(#nick_seguido,#nick_seguidor, fecha

op.borrado(nick_seguido) -CASCADE

op.borrado(nick_seguidores) -CASCADE

  

CLINICA

  

Opciones según la realidad

  

opcion —> PACIENTE (#NSS,nombre,dirección

opcion —> PACIENTE (#NSS,nombre, calle, numero, cp

  

MÉDICO(#num_colegiado,nombre,especialidad,dirección

  

TELÉFONO (#NSS, #teléfono)

  

op.borrado -CASCADE

la clave (paciente, medico) no identifica cada consulta.Posibles opciones

  

CONSULTA (#médico, #paciente, #fecha, diagnóstico)

  

op.borrado(PACIENTE) : CASCADE

op.borrado(MÉDICO) : RESTRICT

  

op —> CONSULTA (#idconsulta, pacienteNN, medicoNN, fecha, diagnósticoç

op—-> CONSULTA (#médico, #paciente, #fecha, #hora  diagnóstico)

  
  

Un mismo paciente puede ir varias veces al mismo médico.Si ¿Basta la clave de las dos entidades para identificar cada consulta? No, no puede duplicarse habría que duplicarla

Si se elimina un paciente, se eliminan sus teléfonos y su historial de consultas. No se puede eliminar a un médico que tenga consultas registradas. 

  

Cadena hotelera

  

HOTEL(#cod_hotel, ciudad, estrellas, nombre

  

HABITACIÓN(#cod_hotel, #num_habitacion, tipo, precio_noche)

op.borrado(cod_hotel) : CASCADE

  

CLIENTE(#dni, nombre teléfono)

  

RESERVA(#cod_hotel, #num_habitacion, #dni, fecha_entrada, fecha_salida)

  

op.borrado(cod_hotel, num_habitacion): RESTRICT

op.borrado(dni): RESTRICT

no valida esta tabla para reservas de la misma habitacion en distinta fechas por el mismo cliente

opción —> RESERVA (#num_reserva, cod_hotelNN, num_habitacionNN, dniNN, fecha_entrada, fecha_salida 

  

Instituto(relación ternaria)

  

PROFESOR(#dni, nombre, departamento)

ASIGNATURA(#cod_asignatura, nombre, horas_semanales)

GRUPO(#cod_grupo, curso, turno

IMPARTE(#cod_grupo,#cod_asignatura, dni, aula)

op.borrado(dni): RESTRICT

op.borrado(cod_asignatura): CASCADE

op.borrado(cod_grupo): CASCADE

  
  

Taller mecánico

  

Clientes(#dni, nombre, multivalor teléfono)

  

Telefonos_clientes(#dni_cliente,#teléfono)

  

op.borrado(dni_cliente):CASCADE

  

Vehículos( #matrícula, marca, modelo, año, #dni_clienteNOT NULL)

  

op.borrado(dni_cliente):RESTRICT

  

Reparación(#codigo, fecha_entrada, fecha_salida, descrip_averia, matriculaNOTNULL, num empleado_encargado NOTNULL, UNIQUE)

  

op.borrado(MATRÍCULA) :CASCADE

op.borrado(num_empleado_encargado): RESTRICT

  

DETALLES( #matricula, #cod_pieza, cantidad)

  

op.borrado(cod_reparacion): CASCADE

op.borrado(cod_pieza): RESTRICT

  

CHECK cantidad > 0

  

Piezas(#ref, descrip, precio)

  

Mecanicos_reparacion(#código, #num_empl, horas)

op.borrado(código): CASCADE

op.borrado(num_empl): RESTRICT  
  

CHECK horas > 0

  

Mecánicos(#num_empl, nombre, categoría)

  

Tienda de routers:

  

Cliente: (#codigo_cliente, nombre, apellidos)

  

Servicio: (#codigo_servicio,codigo_clienteNOT NULL, descripcion, fecha_contratacion, fecha_cancelacion,contrata_seguro)

op.borrado(codigo_cliente):  RESTRICT, por que yo pienso que si un cliente tiene una red asignada no se puede borrar sus datos ya que se perderia la red, y si en el futuro surgen problemas legales se tendría que poder conservar esos datos o para un futuro mejorar la oferta si se va, y no se puede borrar un cliente si tiene servicios

  

Tiendecilla

  

EMPLEADO (#cod_empleado, nombre, apellidos)

  

UBICACION (#cod_ubicacion, planta)

  

OCUPACION (#cod_empleado, cod_ubicaciónNOTNULL UNIQUE)

  

op.borrado(cod_empleado): CASCADE  
op.borrado(cod_ubicacion): CASCADE

  

Prueba

  

PROYECTO(#id_proy, nom_proy, f_inicio, f_fin, dni_jefeNOT NULL)

  

op.borrado(dni_jefe): SET NULL (quitar NOT DEFAULT ´por asignar´

  

EMPLEADO(#dni,nom_empl)

  

op.borrado(id_proy): RESTRICT  
  

ASIG_PROYECTO(#id_proy, #dniNOTNULL, f_inicio, f_fin)

  

op.borrado(id_proy):RESTRICT

op.borrado(dni): CASCADE

  

INMOBILIARIA

  

INMUEBLE(#cod_inmueble, direccion, tamaño)

  

CHALET(#cod_inmueble, plantas, jardín, plazas de garaje)

op.borrado(cod_inmueble): CASCADE, si se vende un chalet se borra todo

  

JUEGO

  

PERSONAJES(#codigo,nombre,descripcion,tipo

  

tipo = {MAGO, GUERRERO}

  

ARQUERO(#codigo)

  

MAGO(#codigo, puntos_magia)

  

op.borrado(codigo): CASCADE

  

GUERRERO(#codigo,puntos_fuerza)

  

HECHIZOS(#nombre,daño,descrip,magia_min)

  

MAGO-HECHIZOS(#codigo_mago, #nombre_hechizo)

op.borrado(codigo_mago): CASCADE (si se borra el mago, se borran la información 

que le asocia a los hechizos

  

op.borrado(nombre_hechizo):CASCADE  
  

ARMA(#nombre, fuerza_minima,daño

  

COPIAS(#nombre_arma,codigo_herrero,#numero)

  

op.borrado(nombre_arma) CASCADE

op.borrado(codigo_herrero): SET NULL

  

CENTRO COMERCIAL:

  

TRABAJADOR(#NIF,nombre,apellidos,salario_base, tipoNN)

tipo=(JEFE,GERENTE,VENDEDOR)

  

JEFES(#NIF trabajador,productividad,)

  

GERENTES(#NIF trabajador,titulación,tipo_gerencia)

  

VENDEDORES(#NIF trabajador,porcentajes,zona_venta

  

op.borrado(NIF_TRABAJADOR): CASCADE

  

DEPARTAMENTO(#cod_departamento,nombre,NIF_TRABAJADORNN, UNIQUE

op.borrado(NIF_TRABAJADOR): RESTRICT

  

PRODUCTO(#cod_producto,precio,unitario,denominación, cod_departamentoNN

op.borrado(cod_departamento): CASCADE

  

VENTA(#num_venta,fecha_venta,NIF_trabajador_vendedorNNcod_producto NNNIF_clienteNN

op.borrado(NIF_trabajador_vendedor): SET DEFAULT ( – )

op.borrado(cod_producto): RESTRICT

op.borrado(nif_cliente): RESTRICT

  

CLIENTE(#NIF,teléfono,nombre)

  

Se incorpora un gerente en nuestra base de datos donde guardamos el gerente, en trabajadores se tendria que poner todos los datos de trabajadores y luego ser especifico en gerente**