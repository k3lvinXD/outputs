# Matemática II Interactiva

Plataforma web educativa para el Proyecto Integrador de **Matemática II (AC2208)** de la UNI. Integra cálculo diferencial de funciones de varias variables, cálculo integral multivariable y análisis vectorial en un flujo único:

`Problema → modelo matemático → desarrollo → gráfica → interpretación → aplicación de ingeniería`

## Capacidades

- Editor visual MathLive con entrada de texto compatible con SymPy.
- Motor simbólico seguro con validación de símbolos, sin uso de `eval()`.
- Desarrollo por pasos: datos implícitos, fórmula, sustitución/desarrollo, resultado e interpretación.
- Gráficas Plotly interactivas de superficies, planos tangentes, campos vectoriales y curvas espaciales.
- Herramientas para parciales, gradiente, direccionales, tangente, extremos, Lagrange, diferenciales exactas, Jacobianos y regla de la cadena.
- Integrales dobles, triples y polares; área de superficie; masa y centro de masa.
- Funciones vectoriales, campos, divergencia, rotacional, laplaciano, integrales de línea, conservatividad y teorema de Green.
- Caso integrador de distribución de temperatura en una placa técnica, ejercicios y un historial de sesión.

## Tecnologías

| Capa | Tecnología |
|---|---|
| Backend | Python 3 y Flask |
| Cálculo | SymPy, NumPy y SciPy |
| Interfaz | HTML5, CSS3, JavaScript y Bootstrap 5 |
| Editor matemático | MathLive (CDN) |
| Renderizado de fórmulas | MathJax (CDN) |
| Visualización | Plotly.js (CDN) |

## Instalación y ejecución

## Abrir y ejecutar en Visual Studio Code

1. Extrae el proyecto y abre la carpeta **matematica_ii_interactiva** con **File → Open Folder** en VS Code.
2. Instala las extensiones recomendadas: **Python** y **Python Debugger** de Microsoft.
3. Abre una terminal integrada (`Ctrl + Ñ`) y crea el entorno virtual con los comandos de la sección correspondiente a tu sistema.
4. Selecciona el intérprete `venv` si VS Code lo solicita.
5. Pulsa **F5** y elige **Iniciar Matemática II Interactiva**. VS Code iniciará `app.py` en su terminal integrada.
6. Abre `http://127.0.0.1:5000` en el navegador.

La carpeta `.vscode` incluida configura automáticamente la depuración para este proyecto.

### Windows (PowerShell)

```powershell
python -m venv venv
venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

Abre [http://127.0.0.1:5000](http://127.0.0.1:5000) en el navegador. Las bibliotecas de interfaz se cargan desde CDN, por lo que se recomienda conexión a Internet al abrir la aplicación.

## Estructura

```text
app.py                 Rutas HTML y API Flask
modules/
  common.py            Entrada segura, serialización y datos de gráficas
  unidad1.py           Cálculo diferencial multivariable
  unidad2.py           Cálculo integral multivariable
  unidad3.py           Análisis vectorial
templates/             Páginas y macro reutilizable de calculadoras
static/css/style.css   Diseño responsive
static/js/main.js      Editor, solicitudes API, Plotly e historial
```

## Uso de las calculadoras

1. Selecciona una unidad o el **Laboratorio Matemático**.
2. Escribe con el editor visual o con sintaxis de texto (`x^2+y^2`, `sqrt(x)`, `sin(theta)`).
3. Completa punto, dirección, límites o restricción cuando la herramienta lo solicite.
4. Pulsa **Calcular** para ver el procedimiento, el resultado simbólico y su aproximación decimal.
5. Usa **Ver gráfica** para una superficie adicional o manipula la gráfica generada con Plotly.

Las expresiones admiten variables `x`, `y`, `z`, `t`, `r`, `theta`, `phi`, `rho` y las funciones `sin`, `cos`, `tan`, `asin`, `acos`, `atan`, `exp`, `log`, `sqrt` y `abs`.

## Seguridad

La aplicación no evalúa código Python escrito por usuarios. Antes de llegar a SymPy, cada expresión se limita en longitud, caracteres, identificadores, variables y funciones; atributos, cadenas, listas y separadores de sentencias no son admisibles. Los errores se devuelven como mensajes amigables, sin traceback.

## Agregar ejercicios

1. Añade el enunciado y la tarjeta visual en `templates/ejercicios.html`.
2. Registra la respuesta simbólica simplificada y la pista en el diccionario `EXERCISES` de `app.py`.
3. El comprobador compara expresiones equivalentes, no solamente texto idéntico.

## Agregar herramientas o problemas de ingeniería

1. Implementa una función de cálculo en el módulo de unidad correspondiente.
2. Incluye su nombre en `OPERATIONS` y `HANDLERS`.
3. Añade una tarjeta con la macro `calculator()` en la plantilla adecuada.
4. Si corresponde, devuelve un `plot` en la respuesta para que `static/js/main.js` lo represente.
5. Acompaña el resultado con interpretación matemática y aplicación ingenieril.

## Personalización de la entrega

En **Acerca del proyecto**, completa facultad, carrera, docente, integrantes y fecha. La sección de bibliografía está deliberadamente vacía para registrar fuentes reales consultadas por el grupo, sin inventar referencias.
