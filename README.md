# Tablas_Creacion_
 
/*==============================================================*/
/* Table: ARMAS                                                 */
/*==============================================================*/
create table ARMAS (
   CODIGO_ARMA          INT4                 not null,
   NOMBRE_ARMA          VARCHAR(30)          null,
   CLASE_ARMA           VARCHAR(30)          null,
   constraint PK_ARMAS primary key (CODIGO_ARMA)
);

/*==============================================================*/
/* Index: ARMAS_PK                                              */
/*==============================================================*/
create unique index ARMAS_PK on ARMAS (
CODIGO_ARMA
);

/*==============================================================*/
/* Table: ARRESTA                                               */
/*==============================================================*/
create table ARRESTA (
   CODIGO_D             INT4                 not null,
   CODIGO_P             INT4                 not null,
   constraint PK_ARRESTA primary key (CODIGO_D, CODIGO_P)
);

/*==============================================================*/
/* Index: ARRESTA_PK                                            */
/*==============================================================*/
create unique index ARRESTA_PK on ARRESTA (
CODIGO_D,
CODIGO_P
);

/*==============================================================*/
/* Index: RELATIONSHIP_7_FK                                     */
/*==============================================================*/
create  index RELATIONSHIP_7_FK on ARRESTA (
CODIGO_P
);

/*==============================================================*/
/* Index: RELATIONSHIP_3_FK                                     */
/*==============================================================*/
create  index RELATIONSHIP_3_FK on ARRESTA (
CODIGO_D
);

/*==============================================================*/
/* Table: CALABOZO                                              */
/*==============================================================*/
create table CALABOZO (
   CODIGO_CALABOZO      INT4                 not null,
   LUGAR_CALABOZO       VARCHAR(40)          null,
   constraint PK_CALABOZO primary key (CODIGO_CALABOZO)
);

/*==============================================================*/
/* Index: CALABOZO_PK                                           */
/*==============================================================*/
create unique index CALABOZO_PK on CALABOZO (
CODIGO_CALABOZO
);

/*==============================================================*/
/* Table: CASO                                                  */
/*==============================================================*/
create table CASO (
   CODIGO_CASO          INT4                 not null,
   JUSGADO              VARCHAR(20)          null,
   constraint PK_CASO primary key (CODIGO_CASO)
);

/*==============================================================*/
/* Index: CASO_PK                                               */
/*==============================================================*/
create unique index CASO_PK on CASO (
CODIGO_CASO
);

/*==============================================================*/
/* Table: DELINCUENTE                                           */
/*==============================================================*/
create table DELINCUENTE (
   CODIGO_D             INT4                 not null,
   CODIGO_CALABOZO      INT4                 null,
   CEDULA_D             VARCHAR(10)          null,
   NOMBRE_D             VARCHAR(40)          null,
   TELEFONO_D           VARCHAR(10)          null,
   constraint PK_DELINCUENTE primary key (CODIGO_D)
);

/*==============================================================*/
/* Index: DELINCUENTE_PK                                        */
/*==============================================================*/
create unique index DELINCUENTE_PK on DELINCUENTE (
CODIGO_D
);

/*==============================================================*/
/* Index: RELATIONSHIP_4_FK                                     */
/*==============================================================*/
create  index RELATIONSHIP_4_FK on DELINCUENTE (
CODIGO_CALABOZO
);

/*==============================================================*/
/* Table: INVESTIGA                                             */
/*==============================================================*/
create table INVESTIGA (
   CODIGO_CASO          INT4                 not null,
   CODIGO_P             INT4                 not null,
   constraint PK_INVESTIGA primary key (CODIGO_CASO, CODIGO_P)
);

/*==============================================================*/
/* Index: INVESTIGA_PK                                          */
/*==============================================================*/
create unique index INVESTIGA_PK on INVESTIGA (
CODIGO_CASO,
CODIGO_P
);

/*==============================================================*/
/* Index: RELATIONSHIP_6_FK                                     */
/*==============================================================*/
create  index RELATIONSHIP_6_FK on INVESTIGA (
CODIGO_P
);

/*==============================================================*/
/* Index: RELATIONSHIP_2_FK                                     */
/*==============================================================*/
create  index RELATIONSHIP_2_FK on INVESTIGA (
CODIGO_CASO
);

/*==============================================================*/
/* Table: POLICIAS                                              */
/*==============================================================*/
create table POLICIAS (
   CODIGO_P             INT4                 not null,
   CEDULA_P             VARCHAR(10)          null,
   NOMBRE_P             VARCHAR(40)          null,
   CATEGORIA_P          VARCHAR(20)          null,
   FUNCION_P            VARCHAR(20)          null,
   constraint PK_POLICIAS primary key (CODIGO_P)
);

/*==============================================================*/
/* Index: POLICIAS_PK                                           */
/*==============================================================*/
create unique index POLICIAS_PK on POLICIAS (
CODIGO_P
);

/*==============================================================*/
/* Table: UTILIZA                                               */
/*==============================================================*/
create table UTILIZA (
   CODIGO_ARMA          INT4                 not null,
   CODIGO_P             INT4                 not null,
   constraint PK_UTILIZA primary key (CODIGO_ARMA, CODIGO_P)
);

/*==============================================================*/
/* Index: UTILIZA_PK                                            */
/*==============================================================*/
create unique index UTILIZA_PK on UTILIZA (
CODIGO_ARMA,
CODIGO_P
);

/*==============================================================*/
/* Index: RELATIONSHIP_5_FK                                     */
/*==============================================================*/
create  index RELATIONSHIP_5_FK on UTILIZA (
CODIGO_P
);

/*==============================================================*/
/* Index: RELATIONSHIP_1_FK                                     */
/*==============================================================*/
create  index RELATIONSHIP_1_FK on UTILIZA (
CODIGO_ARMA
);
