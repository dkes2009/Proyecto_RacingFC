create database BD_Racing_FC
use BD_Racing_FC

create table Deportista(
Pk_id_deportista int identity (1,1) primary key,
nombre_hijo nvarchar (30) not null,
apellido_hijo nvarchar(30) not null,
TI_hijo nvarchar (30) not null,
fecha_nacimiento nvarchar (30) not null,
edad int not null,
Fk_id_inscripcion int foreign key references Inscripcion,
)
create table Inscripcion(
Pk_id_inscripcion int identity(1,1) primary key,
nombre_padre nvarchar(30) not null,
apellido_padre nvarchar(30) not null, 
telefono nvarchar(30) not null,
direccion nvarchar(30) not null,
nombre_hijo nvarchar (30) not null,
apellido_hijo nvarchar (30)not null,
fecha_nacimiento nvarchar(30) not null,
edad int not null,
)

create table categoria_deportista(
id_categoria int identity (1,1) primary key,
nombre_categoria nvarchar(30) not null,
)

create table Ficha_tecnica(
id_ficha int identity (1,1) primary key,
id_categoria int foreign key references categoria_deportista,
id_deportista int foreign key references Deportista,
numero_camisa int not null,
posicion_deportista nvarchar(20),
fecha_nacimiento nvarchar(30) not null,
edad int not null,
)


create table Torneos(
id_torneo int identity(1,1) primary key,
nombre_torneo nvarchar(30) not null,
id_categoria int foreign key references categoria_deportista,
detalle_torneo nvarchar(500),
)


create table partido(
id_partidos int identity (1,1) primary key,
id_torneo int foreign key references Torneos,
fecha_numero_partido nvarchar(30) not null,
fecha_partido nvarchar(30) not null,
ubicacion nvarchar(30) not null,
detalle_partido nvarchar(500) not null,
)

create table tabla_posiciones(
id_tabla_posiciones int identity (1,1) primary key,
id_partido int foreign key references partido,
id_torneo int foreign key references Torneos,
id_categoria int foreign key references  categoria_deportista,
nombre_equipo nvarchar(30)not null,
goles_afavor int not null,
goles_conta int not null,
puntos int not null, 
)


create table Contactanos(
id_contacto int identity (1,1) primary key,
nombre nvarchar(30)not null,
apellido nvarchar(30)not null,
telefono_contacto nvarchar(10)not null,
direccion nvarchar(100) not null,
correo nvarchar(50)not null,
)