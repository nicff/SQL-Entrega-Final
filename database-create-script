CREATE DATABASE bdd_inmobiliaria;

CREATE TABLE inquilinos (
    inq_id VARCHAR(255) PRIMARY KEY,
    inq_nombre VARCHAR(255) NOT NULL,
    inq_documento INT NOT NULL UNIQUE,
    inq_telefono INT NOT NULL,
    inq_email VARCHAR(255) NOT NULL
);

CREATE TABLE propietarios (
    owner_id VARCHAR(255) PRIMARY KEY,
    owner_nombre VARCHAR(255) NOT NULL,
    owner_documento INT NOT NULL UNIQUE,
    owner_telefono INT NOT NULL,
    owner_email VARCHAR(255) NOT NULL
);

CREATE TABLE compradores (
    buyer_id VARCHAR(255) PRIMARY KEY,
    buyer_nombre VARCHAR(255) NOT NULL,
    buyer_documento INT NOT NULL UNIQUE,
    buyer_telefono INT NOT NULL,
    buyer_email VARCHAR(255) NOT NULL
);

CREATE TABLE propiedades (
    prop_id VARCHAR(255) PRIMARY KEY,
    inq_id VARCHAR(255),
    owner_id VARCHAR(255),
    buyer_id VARCHAR(255),
    ubicacion VARCHAR(255) NOT NULL UNIQUE,
    tipo VARCHAR(255) NOT NULL,
    estado VARCHAR(255) NOT NULL,
    valor_alquiler INT,
    valor_venta INT,
    FOREIGN KEY (inq_id) REFERENCES inquilinos(inq_id),
    FOREIGN KEY (owner_id) REFERENCES propietarios(owner_id),
    FOREIGN KEY (buyer_id) REFERENCES compradores(buyer_id)
);


CREATE TABLE contratos (
    contrato_id VARCHAR(255) PRIMARY KEY,
    prop_id VARCHAR(255) NOT NULL,
    owner_id VARCHAR(255) NOT NULL,
    inq_id VARCHAR(255) NOT NULL,
    inicio DATE NOT NULL,
    final DATE NOT NULL,
    valor_alquiler INT NOT NULL,
    FOREIGN KEY (prop_id) REFERENCES propiedades(prop_id),
    FOREIGN KEY (owner_id) REFERENCES propietarios(owner_id),
    FOREIGN KEY (inq_id) REFERENCES inquilinos(inq_id)
);

CREATE TABLE compras (
    compra_id VARCHAR(255) PRIMARY KEY,
    prop_id VARCHAR(255) NOT NULL,
    buyer_id VARCHAR(255) NOT NULL,
    fecha DATE NOT NULL,
    valor_venta INT NOT NULL,
    FOREIGN KEY (prop_id) REFERENCES propiedades(prop_id),
    FOREIGN KEY (buyer_id) REFERENCES compradores(buyer_id)
);

CREATE TABLE reclamos (
    reclamo_id VARCHAR(255) PRIMARY KEY,
    inq_id VARCHAR(255),
    prop_id VARCHAR(255),
    owner_id VARCHAR(255),
    contrato_id VARCHAR(255),
    fecha DATE NOT NULL,
    descripcion VARCHAR(255) NOT NULL,
    estado VARCHAR(255) NOT NULL DEFAULT 'No Resuelto',
    tipo_reclamante INT NOT NULL,
    FOREIGN KEY (inq_id) REFERENCES inquilinos(inq_id),
    FOREIGN KEY (prop_id) REFERENCES propiedades(prop_id),
	FOREIGN KEY (owner_id) REFERENCES propietarios(owner_id),
	FOREIGN KEY (contrato_id) REFERENCES contratos(contrato_id)
);

CREATE TABLE reparymant (
    trabajo_id VARCHAR(255) PRIMARY KEY,
    inq_id VARCHAR(255),
    reclamo_id VARCHAR(255),
    prop_id VARCHAR(255) NOT NULL,
    tipo VARCHAR(255) NOT NULL,
    descripcion VARCHAR(255) NOT NULL,
    estado VARCHAR(255) NOT NULL,
    fecha DATE NOT NULL,
    costo INT,
    FOREIGN KEY (inq_id) REFERENCES inquilinos(inq_id),
    FOREIGN KEY (reclamo_id) REFERENCES reclamos(reclamo_id),
    FOREIGN KEY (prop_id) REFERENCES propiedades(prop_id)
);
