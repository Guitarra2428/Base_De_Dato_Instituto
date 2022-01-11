# Base_De_Dato_Instituto
Esta base de datos se puede implementar para una escuela donde el estudiante podrá solicitar beca universitaria

create DATABASE Institu

USE Institu

Create table Estudiantes(
    EstudianteID INT PRIMARY KEY,
    Nombre VARCHAR(50),
    Apellido VARCHAR(50), 
    Edad int,
    FechaNacimiento  DATE,
    DireccionID INT,
    TelefonoID INT  ,
    CONSTRAINT FK_Direccion FOREIGN key(DireccionID) REFERENCES Direccions(DireccionID),
    CONSTRAINT FK_Telefono FOREIGN key(TelefonoID) REFERENCES Telefonos(TelefonoID)
);
Create TABLE Profesors(
    ProfesorID INT PRIMARY KEY,
    Nombre VARCHAR(50),
    Apellido VARCHAR(50), 
    Edad int,
    FechaNacimiento  DATE ,
    Titulo VARCHAR(30),
    DireccionID INT,
    TelefonoID INT,
     CONSTRAINT FK_PfDireccion FOREIGN key(DireccionID) REFERENCES Direccions(DireccionID),
    CONSTRAINT FK_PfTelefono FOREIGN key(TelefonoID) REFERENCES Telefonos(TelefonoID)
);

Create TABLE Cursos(
    CursoID INT PRIMARY KEY,
    Nombre VARCHAR(30),
    Estatus BIT ,
    Hora INT,
    FechaInicio DATE,
    FechaFinal DATE,
    ProfesorID INT
     CONSTRAINT FK_CuProfesor FOREIGN key(ProfesorID) REFERENCES Profesors(ProfesorID),
    );

    Create table Inscripcions(
    InscripcionID INT PRIMARY KEY,
    Fecha DATE,
    CursoID INT,
    EstudianteID INT,
    CONSTRAINT FK_InCursoID FOREIGN key(CursoID) REFERENCES Cursos(CursoID),
    CONSTRAINT FK_InEstudiante FOREIGN key(EstudianteID) REFERENCES Estudiantes(EstudianteID)
);

Create table BecaUnivercitarias(
    BecaUnivercitariaID INT PRIMARY KEY,
    Nombre VARCHAR(30),
    Instituto VARCHAR(20)
);
Create table SolicitudBecas(
    SolicitudBecaID INT PRIMARY KEY,
    Descripcion VARCHAR(100),
    Fecha DATE,
    EstudianteID INT,
    BecaUnivercitariaID INT
    CONSTRAINT FK_SoEstudiante FOREIGN key(EstudianteID) REFERENCES Estudiantes(EstudianteID),
    CONSTRAINT FK_SoBecaUnivercitariaID FOREIGN key(BecaUnivercitariaID) REFERENCES BecaUnivercitarias(BecaUnivercitariaID),

);

CREATE TABLE Direccions(
    DireccionID INT PRIMARY KEY,
    NombreLugar VARCHAR(30),
    NombreCalle VARCHAR(30),
    NumeroCasa int
)

Create table Telefonos(
    TelefonoID INT PRIMARY key,
    Tipo VARCHAR(30),
    Numero int
)
