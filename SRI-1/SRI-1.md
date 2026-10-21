---
marp: true
theme: default
footer: "<span>Administración de Sistemas Informáticos en Red</span><span>Servicios de Red e Internet</span><span>Profesor: Alfonso Amor Camacho</span>"
transition: slide
style: |

  section {
    background-color: #f8fafc;
    color: #334155; /* Texto normal en gris neutro para una lectura cómoda de la teoría */
    background-image: 
      linear-gradient(135deg, #22c55e 15%, transparent 15%),
      linear-gradient(225deg, #22c55e 15%, transparent 15%),
      linear-gradient(45deg, #22c55e 15%, transparent 15%),
      linear-gradient(315deg, #22c55e 15%, transparent 15%);
    background-position: top left, top right, bottom left, bottom right;
    background-size: 100px 100px;
    background-repeat: no-repeat;
    padding: 70px 80px;
  }

  footer {
    display: flex !important;
    justify-content: space-between !important;
    align-items: center;
    font-size: 0.55em;
    color: #16a34a; /* Verde un poco más claro y vivo para el pie de página */
    border-top: 1px solid #bbf7d0;
    padding-top: 6px;
    width: calc(100% - 160px) !important; 
    position: absolute;
    bottom: 25px;
    left: 80px;
    right: 80px;
  }
  
  h1, h2 {
    color: #16a34a; /* Títulos principales en un verde fresco y más claro */
  }
  
  table.portada-layout, 
  table.portada-layout tr, 
  table.portada-layout td {
    border: none !important;
    background: transparent !important;
  }

  /* ESTILOS FIJOS PARA LA IMAGEN CON CLASE */
  .logo-asir {
    width: 500px;
    border-radius: 16px !important;
    overflow: hidden !important;
    box-shadow: 0 8px 20px rgba(34, 197, 94, 0.4) !important;
    display: inline-block;
  }
  .logo-asir img {
    width: 100% !important;
    height: auto !important;
    display: block !important;
    border-radius: 0 !important;
  }

  /* Forzar centrado absoluto en la tabla de portada */
  table.portada-layout td.col-centrada {
    text-align: center !important;
  }
  table.portada-layout td.col-centrada * {
    text-align: center !important;
  }

  /* Contenedor de dos columnas para índices y contenidos con Grid estricto */
  .index-layout {
    display: grid !important;
    grid-template-columns: 528px 150px 400px !important; /* Lista | Carril de flechas | Tarjeta */
    align-items: center !important;
    gap: 5px !important;
    margin-top: 25px !important;
    width: 100% !important;
  }
  
  .index-col-left {
    flex: 1 !important; /* Columna más ancha para los puntos */
  }
  .index-col-right {
    flex: 1 !important; /* Columna más estrecha para la tarjeta */
  }

  .objective-card {
    background-color: #bce5ca !important;
    border-left: 5px solid #bce5ca !important;
    padding: 15px !important;
    border-radius: 8px !important;
    box-sizing: border-box !important;
    display: flex !important;
    flex-direction: column !important;
    justify-content: center !important;
    align-items: center !important;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4)
  }

  .objective-card p {
    font-size: 0.8em !important;
    margin: 0 !important;
    line-height: 1.5 !important;
    color: #334155 !important;
    text-align: center !important;
  }

  .index-layout ol li a {
    color: inherit;
    text-decoration: none;
    transition: color 0.3s ease, padding-left 0.3s ease; /* Añade suavidad al color */
  }
  .index-layout ol li a:hover {
    color: #16a34a !important; /* Cambia al tono verde principal de tu tema */
    text-decoration: none;
    padding-left: 4px; /* Opcional: desplaza ligeramente el texto hacia la derecha para darle dinamismo */
  }

  /* Transición suave para el enlace de la tarjeta de objetivos */
  .objective-card p a {
    color: inherit;
    text-decoration: none;
    transition: color 0.3s ease;
  }
  .objective-card p a:hover {
    color: #16a34a !important;
    text-decoration: none;
  }

---

# Servicios de Configuración Automática en la Red
### Automatización e integración del direccionamiento en redes IPv4 e IPv6

<table class="portada-layout" style="width: 100%; margin-top: 20px;">
  <tr>
    <td class="col-centrada" style="width: 55%; vertical-align: middle; padding: 0 20px;">
      <h3 style="color: #16a34a; font-size: 1.25em; line-height: 1.4; margin: 0;">
        ¿Cómo logramos que cientos de dispositivos se conecten, configuren y comuniquen de forma autónoma sin intervención manual?
      </h3>
    </td>
    <td style="width: 45%; text-align: center; vertical-align: middle;">
      <div class="logo-asir">
        <img src="SRI.jpg" />
      </div>
    </td>
  </tr>
</table>

---

# Servicios de Configuración Automática en la Red
### Contenidos de la Unidad

<div class="index-layout">

  <!-- Columna 1: Lista de contenidos -->
  <div>
    <ol style="margin: 0; padding-left: 20px; font-size: 0.85em; line-height: 1.8;">
      <li style="margin-bottom: 12px;"><a href="#funcionamiento-de-los-servicios">Funcionamiento de los servicios</a></li>
      <li style="margin-bottom: 12px;"><a href="#evolución-de-dhcp-a-slaac">Evolución de DHCP a SLAAC</a></li>
      <li style="margin-bottom: 12px;"><a href="#asignaciones-estáticas-y-dinámicas">Asignaciones estáticas y dinámicas</a></li>
      <li style="margin-bottom: 12px;"><a href="#bloques-parámetros-y-declaraciones">Bloques, parámetros y declaraciones</a></li>
      <li style="margin-bottom: 12px;"><a href="#administración-práctica-del-servidor">Administración práctica del servidor</a></li>
    </ol>
  </div>
  
  <!-- Columna 2: Carril central con las flechas -->
  <div style="display: flex; align-items: center; justify-content: center;">
    <img src="data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='150' height='260' viewBox='0 0 140 260'><defs><marker id='arrow' viewBox='0 0 10 10' refX='6' refY='5' markerWidth='6' markerHeight='6' orient='auto-start-reverse'><path d='M 0 0 L 10 5 L 0 10 z' fill='%2316a34a'/></marker></defs><line x1='-15' y1='25' x2='140' y2='100' stroke='%2316a34a' stroke-width='2' marker-end='url(%23arrow)'/><line x1='-15' y1='75' x2='140' y2='115' stroke='%2316a34a' stroke-width='2' marker-end='url(%23arrow)'/><line x1='-15' y1='130' x2='140' y2='130' stroke='%2316a34a' stroke-width='2' marker-end='url(%23arrow)'/><line x1='-15' y1='185' x2='140' y2='145' stroke='%2316a34a' stroke-width='2' marker-end='url(%23arrow)'/><line x1='-15' y1='235' x2='140' y2='160' stroke='%2316a34a' stroke-width='2' marker-end='url(%23arrow)'/></svg>" style="width: 100px; height: auto; display: block;" />
  </div>

  <!-- Columna 3: Tarjeta de objetivo con la clase CSS limpia -->
  <div>
    <div class="objective-card">
      <p>
        <a href="#resumen">Conseguir desplegar infraestructuras de red autónomas, eliminando por completo la intervención manual en entornos locales</a>
      </p>
    </div>
  </div>

</div>

---

# Funcionamiento de los Servicios
### Introducción Teórica: De la estática a la automatización

<div style="display: flex; justify-content: space-around; align-items: center; margin-top: 50px; text-align: center;">

  <div style="background: #fee2e2; border: 2px solid #ef4444; padding: 25px; border-radius: 12px; width: 30%;">
    <h3 style="color: #dc2626; margin-top: 0;">Configuración Manual</h3>
    <p style="font-size: 0.75em; margin: 0; color: #7f1d1d;">
      Asignación estática por equipo.<br>
      <strong>Alto riesgo de error humano</strong> y sobrecarga en redes medianas.
    </p>
  </div>

  <div style="font-size: 2.5em; color: #16a34a; font-weight: bold;">
    ➔
  </div>

  <div style="background: #dcfce7; border: 2px solid #22c55e; padding: 25px; border-radius: 12px; width: 32%;">
    <h3 style="color: #16a34a; margin-top: 0;">Configuración Dinámica</h3>
    <p style="font-size: 0.75em; margin: 0; color: #14532d;">
      Asignación centralizada y autónoma.<br>
      <strong>Garantía de unicidad</strong> y despliegue inmediato.
    </p>
  </div>

</div>

<div style="text-align: center; margin-top: 40px;">
  <p style="font-size: 0.8em; color: #64748b; font-style: italic;">
    Objetivo: Proveer parámetros de red de forma transparente para el usuario final.
  </p>
</div>

---

# Funcionamiento de los Servicios
Contenido del apartado 1...

---

# Funcionamiento de los Servicios
Contenido del apartado 1...

---

# Funcionamiento de los Servicios
Contenido del apartado 1...

---

# Funcionamiento de los Servicios
Contenido del apartado 1...

---

# Evolución de DHCP a SLAAC
Contenido del apartado 2...

---

# Evolución de DHCP a SLAAC
Contenido del apartado 2...

---

# Evolución de DHCP a SLAAC
Contenido del apartado 2...

---

# Evolución de DHCP a SLAAC
Contenido del apartado 2...

---

# Evolución de DHCP a SLAAC
Contenido del apartado 2...

---

# Asignaciones Estáticas y Dinámicas
Contenido del apartado 3...

---

# Asignaciones Estáticas y Dinámicas
Contenido del apartado 3...

---

# Asignaciones Estáticas y Dinámicas
Contenido del apartado 3...

---

# Asignaciones Estáticas y Dinámicas
Contenido del apartado 3...

---

# Asignaciones Estáticas y Dinámicas
Contenido del apartado 3...

---

# Bloques, Parámetros y Declaraciones
Contenido del apartado 4...

---

# Bloques, Parámetros y Declaraciones
Contenido del apartado 4...

---

# Bloques, Parámetros y Declaraciones
Contenido del apartado 4...

---

# Bloques, Parámetros y Declaraciones
Contenido del apartado 4...

---

# Bloques, Parámetros y Declaraciones
Contenido del apartado 4...

---

# Bloques, Parámetros y Declaraciones
Contenido del apartado 4...

---

# Administración Práctica del Servidor
Contenido del apartado 5...

---

# Administración Práctica del Servidor
Contenido del apartado 5...

---

# Administración Práctica del Servidor
Contenido del apartado 5...

---

# Administración Práctica del Servidor
Contenido del apartado 5...

---

# Administración Práctica del Servidor
Contenido del apartado 5...

---

# Administración Práctica del Servidor
Contenido del apartado 5...

---

# Resumen
Contenido del resumen...

