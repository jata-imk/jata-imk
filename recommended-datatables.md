Sí, hay varias bibliotecas de JavaScript que pueden mostrar tablas de datos y permitir la selección de celdas, filas o columnas para copiar y pegar, al estilo de Excel. Aquí te menciono algunas opciones muy populares que te permiten hacerlo:

### 1. **Handsontable**
[Handsontable](https://handsontable.com/) es una de las bibliotecas más robustas para trabajar con tablas de datos en JavaScript, con muchas características similares a las hojas de cálculo de Excel, como la edición de celdas, selección de filas/columnas, y copiar/pegar.

#### Características:
- Selección de celdas, filas o columnas.
- Soporta copiar y pegar directamente al portapapeles, compatible con Excel.
- Edición en línea, formato condicional, validación de datos.
- Soporte para grandes volúmenes de datos.
- Extensible con plugins para funcionalidad adicional.

#### Ejemplo básico:
```html
<div id="example"></div>
<script>
  const data = [
    ["", "Ford", "Volvo", "Toyota", "Honda"],
    ["2016", 10, 11, 12, 13],
    ["2017", 20, 11, 14, 13],
    ["2018", 30, 15, 12, 13]
  ];

  const container = document.getElementById('example');
  const hot = new Handsontable(container, {
    data: data,
    rowHeaders: true,
    colHeaders: true,
    contextMenu: true,
    copyPaste: true, // Habilita la función de copiar/pegar
    selectionMode: 'multiple',
  });
</script>
```

### 2. **DataTables**
[DataTables](https://datatables.net/) es otra biblioteca muy popular para mostrar tablas de datos en aplicaciones web. Si bien no tiene la funcionalidad de Excel por defecto, puedes extenderla para habilitar la selección de celdas, y existen plugins que añaden funcionalidades como copiar/pegar al estilo de Excel.

#### Características:
- Tablas responsivas y personalizables.
- Extensible con muchos plugins para funcionalidades avanzadas.
- Soporte para exportación (PDF, Excel, CSV) y otras características útiles para copiar datos.
- Posibilidad de seleccionar filas o celdas y copiar datos.

#### Plugin para copiar datos:
Puedes usar el complemento `Buttons` para agregar la funcionalidad de copiar datos fácilmente al portapapeles.

```html
<link rel="stylesheet" href="https://cdn.datatables.net/1.11.5/css/jquery.dataTables.min.css">
<link rel="stylesheet" href="https://cdn.datatables.net/buttons/2.1.0/css/buttons.dataTables.min.css">

<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://cdn.datatables.net/1.11.5/js/jquery.dataTables.min.js"></script>
<script src="https://cdn.datatables.net/buttons/2.1.0/js/dataTables.buttons.min.js"></script>
<script src="https://cdn.datatables.net/buttons/2.1.0/js/buttons.html5.min.js"></script>

<table id="example" class="display" style="width:100%">
  <thead>
    <tr>
      <th>Name</th>
      <th>Position</th>
      <th>Office</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Tiger Nixon</td>
      <td>System Architect</td>
      <td>Edinburgh</td>
      <td>61</td>
    </tr>
    <!-- Más filas -->
  </tbody>
</table>

<script>
  $(document).ready(function() {
    $('#example').DataTable({
      dom: 'Bfrtip',
      buttons: [
        'copy'
      ]
    });
  });
</script>
```

### 3. **AG Grid**
[AG Grid](https://www.ag-grid.com/) es otra biblioteca muy avanzada y flexible para mostrar datos en tablas. Tiene características de selección de celdas, filas o columnas, y también soporta la funcionalidad de copiar/pegar similar a Excel.

#### Características:
- Copiar y pegar datos desde celdas seleccionadas.
- Permite trabajar con grandes conjuntos de datos.
- Selección de celdas, filas, columnas.
- Funciones avanzadas como filtrado, agrupación y exportación a CSV o Excel.

#### Ejemplo básico:
```html
<div id="myGrid" style="height: 150px; width:600px;" class="ag-theme-alpine"></div>

<script src="https://unpkg.com/ag-grid-community/dist/ag-grid-community.min.noStyle.js"></script>
<script>
  var columnDefs = [
    { headerName: "Make", field: "make" },
    { headerName: "Model", field: "model" },
    { headerName: "Price", field: "price" }
  ];

  var rowData = [
    { make: "Toyota", model: "Celica", price: 35000 },
    { make: "Ford", model: "Mondeo", price: 32000 },
    { make: "Porsche", model: "Boxster", price: 72000 }
  ];

  var gridOptions = {
    columnDefs: columnDefs,
    rowData: rowData,
    enableRangeSelection: true, // Habilita la selección de rango
    enableClipboard: true // Habilita la funcionalidad de copiar/pegar
  };

  var eGridDiv = document.querySelector('#myGrid');
  new agGrid.Grid(eGridDiv, gridOptions);
</script>
```

### 4. **Tabulator**
[Tabulator](http://tabulator.info/) es otra opción poderosa que permite mostrar datos en tablas interactivas. Tiene soporte integrado para copiar/pegar celdas y otras características avanzadas como edición en línea y exportación.

#### Características:
- Soporte para copiar y pegar celdas, filas o columnas.
- Tablas editables.
- Exportación a CSV, JSON, y más.
- Funcionalidades avanzadas como filtros, paginación, agrupación.

#### Ejemplo básico:
```html
<link href="https://unpkg.com/tabulator-tables@5.0.7/dist/css/tabulator.min.css" rel="stylesheet">
<script src="https://unpkg.com/tabulator-tables@5.0.7/dist/js/tabulator.min.js"></script>

<div id="example-table"></div>

<script>
var table = new Tabulator("#example-table", {
  data:[
    {id:1, name:"Oli Bob", age:"12", col:"red", dob:""},
    {id:2, name:"Mary May", age:"1", col:"blue", dob:"14/05/1982"},
    {id:3, name:"Christine Lobowski", age:"42", col:"green", dob:"22/05/1982"},
  ],
  columns:[
    {title:"Name", field:"name"},
    {title:"Age", field:"age"},
    {title:"Favourite Color", field:"col"},
  ],
  clipboard:true, // Habilita el copiar/pegar
});
</script>
```

### Conclusión
Todas estas bibliotecas permiten trabajar con tablas de datos y tienen soporte para copiar y pegar al estilo de Excel. Si buscas algo simple y directo, `Tabulator` y `AG Grid` son opciones muy flexibles. Si necesitas una funcionalidad más avanzada y parecida a Excel, `Handsontable` es probablemente la mejor opción.

¿Te gustaría más detalles sobre alguna de estas opciones?
