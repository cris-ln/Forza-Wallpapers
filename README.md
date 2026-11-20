# Forza Wallpapers 🏎️

Aplicación descentralizada (dApp) para crear galerías y publicar wallpapers de vehículos de Forza Horizon 5 y Forza Motorsport mediante Solana.

## 1. Objetivo del proyecto

Forza Wallpapers permite a los usuarios administrar una galería de wallpapers vinculada a su wallet de Solana.

El proyecto busca combinar una temática automotriz con tecnología blockchain, utilizando cuentas y direcciones derivadas de programa (PDAs) para almacenar y administrar la información.

## 2. Ruta del proyecto

**Proyecto propio:** desarrollo de una aplicación descentralizada sobre Solana utilizando Anchor, React y TypeScript.

## 3. Tecnologías utilizadas

- Solana y Solana Devnet.
- Rust.
- Anchor Framework 0.31.1.
- React.
- TypeScript.
- Vite.
- Solana Wallet Adapter.
- Phantom y Solflare.
- Instagram Embeds para mostrar las publicaciones asociadas a los wallpapers.

## 4. Funcionalidades del programa

El contrato inteligente permite:

- Crear una galería asociada a una wallet.
- Publicar wallpapers con título, juego, URL y precio.
- Consultar la información de las galerías y wallpapers.
- Actualizar el precio de un wallpaper.
- Eliminar un wallpaper mediante una instrucción autorizada.

El precio se almacena como información del wallpaper. El programa no procesa pagos ni realiza transferencias de SOL por las publicaciones.

## 5. Arquitectura y seguridad

El programa utiliza dos tipos de cuentas:

**Galería**
- Identifica al propietario.
- Almacena el nombre de la galería.
- Mantiene el contador de wallpapers.

**Wallpaper**
- Identifica al propietario y a su galería.
- Almacena el identificador, título, juego, URL, precio y descargas.

Se utilizan PDAs para derivar las direcciones de las cuentas:

- Galería: `["galeria", owner]`
- Wallpaper: `["wallpaper", galeria, id]`

Las instrucciones incorporan validaciones para proteger la integridad de los datos y restringir las operaciones al propietario autorizado.

La eliminación de un wallpaper cierra su cuenta y devuelve la renta al propietario.

## 6. Programa desplegado en Devnet

**Program ID:**

`CpvzJ6dcKsmfZMAnmhyx8vs3H8UjEbQnnzzPN1b7RDcC`

Red: Solana Devnet.

[Consultar el programa en Solana Explorer](https://explorer.solana.com/address/CpvzJ6dcKsmfZMAnmhyx8vs3H8UjEbQnnzzPN1b7RDcC?cluster=devnet)

## 7. Instalación y ejecución

### Requisitos

- Node.js 20 LTS.
- Yarn.
- Solana CLI.
- Anchor CLI 0.31.1.
- Rust y Cargo.

### Frontend

Desde la terminal:

```bash
cd app
npm install
npm run dev
```

Abrir en el navegador la dirección local que proporcione Vite, normalmente `http://localhost:5173/`.

Conectar una wallet compatible configurada en Devnet.

### Pruebas del programa

Desde la raíz del proyecto:

```bash
anchor test --provider.cluster localnet --skip-lint
```

Este comando ejecuta las pruebas automatizadas en Localnet.

## 8. Pruebas realizadas

Se ejecutó una prueba automatizada que comprueba:

- Creación de galería.
- Rechazo de título vacío.
- Rechazo de URL demasiado larga.
- Publicación válida de un wallpaper.
- Actualización del precio.
- Rechazo de modificaciones realizadas por otra wallet.
- Rechazo de eliminación realizada por otra wallet.
- Eliminación autorizada por el propietario.

**Resultado obtenido:**

`1 passing (2s)`

Las comprobaciones finalizaron correctamente en Localnet.

La evidencia de ejecución se conserva en `evidencia-pruebas-localnet.txt`.

## 9. Contribución personal

El proyecto fue desarrollado como una propuesta propia enfocada en el catálogo de wallpapers de Forza.

La contribución comprende el diseño y desarrollo del programa en Rust con Anchor, la definición de cuentas y PDAs, las validaciones de seguridad y propiedad, las instrucciones de administración, las pruebas automatizadas y la integración de un frontend en React y TypeScript con conexión a wallets de Solana.

También se desarrolló la presentación visual del catálogo y la integración de publicaciones de Instagram.

## 10. Estado del proyecto

El programa está desplegado en Solana Devnet y cuenta con pruebas automatizadas aprobadas en Localnet.

El frontend está preparado para conectarse a Devnet mediante una wallet compatible.