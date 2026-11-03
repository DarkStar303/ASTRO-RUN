# ASTRO RUN — Portal Oficial y Videojuego Endless Runner 3D (Unity WebGL)

**ASTRO RUN** es un videojuego de carrera infinita en tres dimensiones (*Endless Runner 3D*) desarrollado en **Unity 6000.6.0f1** y desplegado en la web mediante **WebGL 2.0 / WebAssembly**, acompañado de su portal interactivo oficial de divulgación técnica y promoción.

El jugador toma el control de **ASTRO**, un robot explorador universitario que avanza a través de una pasarela espacial continua desde la órbita de la **Tierra** hasta el sistema de anillos de **Saturno**, esquivando amenazas orbitales mediante reflejos rápidos para alcanzar la meta de la misión.

## Autores y Créditos del Proyecto

| Campo | Detalle |
| :--- | :--- |
| **Creadores y Desarrolladores** | **José Alejandro Salazar Quiroga** y **Julio Mateo Bustillos Serrano** |
| **Institución Académica** | Universidad Privada del Valle (UPV — Bolivia) |
| **Asignatura** | Game Development (Unidad 2: Scripting y Matemáticas · Unidad 3: Portafolio del Juego) |
| **Motor y Tecnología** | Unity 6000.6.0f1 (C#) · Compilación WebGL 2.0 · Portal en HTML5, CSS3 y JavaScript |
| **Género** | Endless Runner 3D · Arcade de reflejos y esquiva en tercera persona |

## Historia y Secuencia Narrativa (Storytelling)

La misión de **ASTRO RUN** se desarrolla a través de dos regiones del sistema solar conectadas en una misma travesía continua:

1. **Fase 01 — Órbita de la Tierra (`0 m` a `600 m`)**: El recorrido inicia sobre una plataforma orbital metálica iluminada con luces azules, con la curvatura terrestre visible en el horizonte. Durante este tramo, ASTRO debe saltar sobre satélites de mantenimiento bajos y agacharse ante cohetes que cruzan a la altura de la cabeza.
2. **Fase 02 — Anillos de Saturno (a partir de `600 m`)**: Al superar los 600 metros de distancia, el escenario se transforma hacia Saturno y su sistema de anillos, adoptando tonos minerales y luces cálidas. Las amenazas evolucionan hacia rocas de los anillos (obstáculos bajos) y meteoritos suspendidos (obstáculos elevados).

| Etapa | Acción Narrativa | Comunicación en Pantalla |
| :--- | :--- | :--- |
| **01. Entrada (Despegue)** | ASTRO se prepara para investigar el espacio a bordo de su ruta orbital. | Pantalla de inicio con título, instrucciones y botón **«INICIAR MISIÓN»**. |
| **02. Motivación** | Recorre grandes distancias esquivando amenazas procedurales para sumar puntos. | Marcador de puntaje en tiempo real, indicador de 3 vidas y distancia en metros. |
| **03. Cambio de Fase** | Al alcanzar los **600 m** ingresa al entorno de los anillos de Saturno. | Transición planetaria, cambio de paleta cromática y nuevos obstáculos. |
| **04. Éxito (Victoria)** | Al conseguir **1.500 puntos**, la misión culmina satisfactoriamente. | Panel **«¡MISIÓN COMPLETADA!»**, registro de récord y opción de reinicio (`R`). |
| **05. Derrota** | Si pierde las **3 vidas**, el robot cae y concluye la exploración espacial. | Animación `MORIR`, pantalla **«MISIÓN TERMINADA»**, puntaje final y reinicio (`R`). |

## Personaje Principal (`ASTRO`) y Dirección Artística

- **Concepto visual**: Robot explorador modelado en 3D bajo una dirección artística *Sci-Fi Cartoon* de geometrías redondeadas, silueta legible y alto contraste frente al entorno estelar.
- **Identidad institucional**: Porta el emblema oficial de la **Universidad Privada del Valle (UPV — Bolivia)** en el pecho y en el módulo de su mochila espacial.
- **Paleta cromática**: Casco y extremidades en tono burdeos (`#822e51`), fuselaje cerámico en acero gris (`#afb2b8`), visor facial negro brillante (`#171920`), ojos LED blancos (`#edf7ff`) y acentos luminosos en cian (`#74e6f4`).
- **Máquina de Estados (`Animator Controller`)**: Integra 4 estados de animación conectados en Unity:
  - `CORRER`: Ciclo base de desplazamiento continuo sobre la pista.
  - `SALTAR`: Impulso vertical con física y gravedad para superar obstáculos bajos.
  - `AGACHARSE`: Postura baja durante `0,85 segundos` que reduce proporcionalmente la altura física del `CapsuleCollider` para pasar debajo de amenazas altas.
  - `MORIR`: Secuencia ejecutada cuando el contador de vidas llega a cero.

## Controles del Videojuego

| Entrada / Tecla | Acción en el Juego | Descripción Técnica |
| :--- | :--- | :--- |
| **Clic en «INICIAR MISIÓN»** | Despegar / Iniciar | Inicia la partida desde la pantalla de bienvenida dentro del lienzo WebGL. |
| **Flecha Arriba (`↑`)** o **Espacio (`SPACE`)** | Saltar | Eleva a ASTRO en el aire para esquivar satélites bajos y rocas de los anillos. |
| **Flecha Abajo (`↓`)** o **Tecla `S`** | Agacharse | Agacha al personaje durante `0,85 s` y reduce su `CapsuleCollider` ante cohetes y meteoritos. |
| **Tecla `ESC`** | Pausar | Pausa la partida en curso y despliega la opción para reanudar la exploración. |
| **Tecla `R`** | Reiniciar | Reinicia inmediatamente la misión tras alcanzar la victoria o perder las 3 vidas. |

## Clasificación de Obstáculos

| Elemento / Amenaza | Escenario | Categoría | Acción Requerida |
| :--- | :--- | :--- | :--- |
| **Satélite de mantenimiento** | Fase 01 · Tierra | Obstáculo Bajo | Saltar (`↑` o `Espacio`) |
| **Cohete de paso elevado** | Fase 01 · Tierra | Obstáculo Alto | Agacharse (`↓` o `S`) |
| **Rocas de los anillos** | Fase 02 · Saturno | Obstáculo Bajo | Saltar (`↑` o `Espacio`) |
| **Meteorito suspendido** | Fase 02 · Saturno | Obstáculo Alto | Agacharse (`↓` o `S`) |

## Métricas de Diseño y Ficha Técnica (GDD)

| Parámetro del Sistema | Valor Configurado | Comportamiento en el Motor |
| :--- | :--- | :--- |
| **Meta de Victoria** | `1.500 puntos` | Detiene la carrera y despliega el estado **«¡MISIÓN COMPLETADA!»**. |
| **Distancia de Transición** | `600 metros` | Cambia el escenario activo de la órbita de la Tierra a los anillos de Saturno. |
| **Vidas Iniciales** | `3 vidas` | Cada colisión resta 1 vida y activa inmunidad temporal contra impactos dobles. |
| **Puntaje por Supervivencia** | `+10 puntos / segundo` | Incremento continuo mientras el personaje se mantiene con vida. |
| **Bonificación por Esquive** | `+5 puntos / obstáculo` | Otorgado al superar cada amenaza sin recibir daño. |
| **Velocidad y Aceleración** | `12 u/s` → `29 u/s` (`+0,11 u/s²`) | Incrementa progresivamente la velocidad y reduce el intervalo de aparición de obstáculos. |
| **Limpieza de Escenario** | Automática tras cámara | Destruye los obstáculos que quedan detrás de la vista del jugador para optimizar memoria. |

## Estructura del Repositorio

```text
├── index.html                  # Portal web oficial con reproductor WebGL incrustado, historia, visor 3D y métricas
├── .nojekyll                   # Configuración para servir archivos WebAssembly (.wasm) sin filtros de Jekyll en GitHub Pages
├── README.md                   # Documentación técnica y guía del repositorio
├── imagenes/                   # Vistas renderizadas del modelo 3D original de ASTRO (.webp)
│   ├── astro_frontal.webp
│   ├── astro_perfil.webp
│   ├── astro_espalda.webp
│   └── astro_accion.webp
└── juego/                      # Compilación oficial de Unity WebGL
    ├── index.html              # Contenedor de ejecución de Unity Web Player
    ├── manifest.webmanifest    # Manifiesto de aplicación web
    ├── ServiceWorker.js        # Caché de recursos del motor
    ├── Build/                  # Binarios y scripts de ejecución del juego
    │   ├── Astro_run_web.data
    │   ├── Astro_run_web.framework.js
    │   ├── Astro_run_web.loader.js
    │   └── Astro_run_web.wasm
    └── TemplateData/           # Estilos e íconos de la pantalla de carga de Unity
```

## Requisitos y Ejecución

1. **Desde GitHub Pages (Recomendado)**: Accede al enlace público del repositorio desplegado en GitHub Pages, desplázate hasta la sección **05 / Despliegue y Ejecución («Jugar ahora»)** y haz clic sobre **«INICIAR MISIÓN»** dentro de la terminal interactiva (o usa el botón **«⛶ Pantalla Completa»**).
2. **En entorno local**: Debido a las políticas de seguridad de los navegadores modernos para archivos `WebAssembly (.wasm)`, la compilación no debe abrirse mediante protocolo `file://` (doble clic). Para probarlo localmente, ejecuta un servidor HTTP local en la raíz del proyecto (por ejemplo, `python -m http.server 8000` o la extensión *Live Server* de VS Code) y abre `http://localhost:8000`.
3. **Requisitos mínimos del navegador**: Navegador de escritorio actualizado (Google Chrome, Microsoft Edge, Mozilla Firefox o Brave) con soporte para **WebGL 2.0** y aceleración por hardware activada.
