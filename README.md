# Villamora-s-repository
Clase de introducción a la programación 
-- phpMyAdmin SQL Dump
-- version 5.2.1
-- https://www.phpmyadmin.net/
--
-- Servidor: 127.0.0.1
-- Tiempo de generación: 05-04-2025 a las 03:43:13
-- Versión del servidor: 10.4.32-MariaDB
-- Versión de PHP: 8.2.12

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Base de datos: `prestamos_de_computadores`
--

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `equipos`
--

CREATE TABLE `equipos` (
  `ID_equipo` int(11) NOT NULL,
  `Nombre_equipo` varchar(30) DEFAULT NULL,
  `Tipo_equipo` varchar(30) DEFAULT NULL,
  `Marca` varchar(20) DEFAULT NULL,
  `Modelo` year(4) DEFAULT NULL,
  `ID_sede` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Volcado de datos para la tabla `equipos`
--

INSERT INTO `equipos` (`ID_equipo`, `Nombre_equipo`, `Tipo_equipo`, `Marca`, `Modelo`, `ID_sede`) VALUES
(555, 'Lapto_01', 'Diseño_grafico', 'Hp', '2022', 1234);

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `prestamos`
--

CREATE TABLE `prestamos` (
  `ID_prestamo` int(11) NOT NULL,
  `ID_usuario` int(11) DEFAULT NULL,
  `ID_equipo` int(11) DEFAULT NULL,
  `Fecha_prestamo` date DEFAULT NULL,
  `Hora_prestamo` time DEFAULT NULL,
  `Fecha_devolucion` date DEFAULT NULL,
  `Hora_devolucion` time DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Volcado de datos para la tabla `prestamos`
--

INSERT INTO `prestamos` (`ID_prestamo`, `ID_usuario`, `ID_equipo`, `Fecha_prestamo`, `Hora_prestamo`, `Fecha_devolucion`, `Hora_devolucion`) VALUES
(666, 1002345678, 555, '2025-02-09', '12:00:00', '2025-02-12', '12:00:00');

-- --------------------------------------------------------

--
-- Estructura de tabla para la tabla `usuarios`
--

CREATE TABLE `usuarios` (
  `ID_usuario` int(11) NOT NULL,
  `Nombre` varchar(20) DEFAULT NULL,
  `Apellido` varchar(30) DEFAULT NULL,
  `Correo_electronico` varchar(30) DEFAULT NULL,
  `Telefono` varchar(20) DEFAULT NULL,
  `ID_carrera` int(11) DEFAULT NULL,
  `Estado_usuario` enum('Activo','Inactivo') DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Volcado de datos para la tabla `usuarios`
--

INSERT INTO `usuarios` (`ID_usuario`, `Nombre`, `Apellido`, `Correo_electronico`, `Telefono`, `ID_carrera`, `Estado_usuario`) VALUES
(248101214, '[felipe]', '[duque]', '[feliped@gmail.com]', '[6078888]', 2345, 'Activo'),
(446789007, '[duvan]', '[cardenas]', '[duvanc@gmail.com]', '[6779955]', 2345, 'Inactivo'),
(1000444534, '[manuel]', '[perez]', '[manuelp@gmail.com]', '[6181920]', 3344, 'Inactivo'),
(1002345678, 'Juan ', 'Castro', 'juan@gmail.com', '123456789', 77777, 'Activo'),
(1005448466, '[antonio]', '[ramos]', '[antonior@gmail.com]', '[6046789]', 3344, 'Activo'),
(1435667789, '[maria]', '[perez]', '[mariap@gmail.com]', '[6170054]', 3344, 'Activo'),
(2147483647, '[daniel]', '[jaimes]', '[danielj@gmail.com]', '[6578910]', 77777, 'Inactivo');

--
-- Índices para tablas volcadas
--

--
-- Indices de la tabla `equipos`
--
ALTER TABLE `equipos`
  ADD PRIMARY KEY (`ID_equipo`);

--
-- Indices de la tabla `prestamos`
--
ALTER TABLE `prestamos`
  ADD PRIMARY KEY (`ID_prestamo`),
  ADD KEY `ID_usuario` (`ID_usuario`),
  ADD KEY `ID_equipo` (`ID_equipo`);

--
-- Indices de la tabla `usuarios`
--
ALTER TABLE `usuarios`
  ADD PRIMARY KEY (`ID_usuario`);

--
-- Restricciones para tablas volcadas
--

--
-- Filtros para la tabla `prestamos`
--
ALTER TABLE `prestamos`
  ADD CONSTRAINT `prestamos_ibfk_1` FOREIGN KEY (`ID_usuario`) REFERENCES `usuarios` (`ID_usuario`),
  ADD CONSTRAINT `prestamos_ibfk_2` FOREIGN KEY (`ID_equipo`) REFERENCES `equipos` (`ID_equipo`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
