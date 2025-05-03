# registro-
registro de empresa 
<?php
include 'conexion.php';

// Verificar si los datos fueron enviados
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $nombre = $_POST['nombre_empresa'];
    $representante = $_POST['representante_legal'];
    $categoria = $_POST['categoria_empresa'];
    $nit = $_POST['nit'];
    $telefono = $_POST['telefono'];
    $correo = $_POST['correo'];
    $direccion = $_POST['direccion'];

    $sql = "INSERT INTO empresas (nombre_empresa, representante_legal, categoria, nit, telefono, correo, direccion)
            VALUES ('$nombre', '$representante', '$categoria', '$nit', '$telefono', '$correo', '$direccion')";

    if ($conexion->query($sql) === TRUE) {
        header("Location: index.php?mensaje=ok");
        exit();
    } else {
        header("Location: index.php?mensaje=error");
        exit();
    }

    $conexion->close();
}
?>
