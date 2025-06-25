# Cooking-list-zelda
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Recetas de Cocina – Zelda: Tears of the Kingdom</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; }
    input, select { margin: 5px; padding: 5px; }
    table { width: 100%; border-collapse: collapse; margin-top: 10px; }
    th, td { border: 1px solid #ccc; padding: 8px; text-align: left; }
    th { background: #f0f0f0; }
  </style>
</head>
<body>
  <h1>Recetas de Cocina – Tears of the Kingdom</h1>

  <div>
    <label>Buscar por ingrediente:</label>
    <input id="ingrediente" placeholder="e.g. Mighty Banana">
    <label>Filtrar por efecto:</label>
    <select id="efecto">
      <option value="">--Todos--</option>
      <option value="Attack Up">Attack Up</option>
      <option value="Cold Resistance">Cold Resistance</option>
      <option value="Flame Guard">Flame Guard</option>
      <!-- etc. -->
    </select>
    <button onclick="buscar()">Buscar</button>
  </div>

  <table id="tabla">
    <thead>
      <tr>
        <th>Receta</th><th>Ingredientes</th><th>Efecto</th><th>Duración estimada</th>
      </tr>
    </thead>
    <tbody></tbody>
  </table>

  <script>
    // Ejemplo de base de datos
    const recetas = [
      {
        nombre: "Mighty Elixir",
        ingredientes: ["Bladed Rhino Beetle", "Monster Part"],
        efecto: "Attack Up",
        duracion: "≈3:30 (base + bonus)", 
      },
      {
        nombre: "Spicy Elixir",
        ingredientes: ["Summerwing Butterfly", "Monster Part"],
        efecto: "Cold Resistance",
        duracion: "≈3–5 minutos según partes", 
      },
      {
        nombre: "Sneaky Elixir",
        ingredientes: ["Sunset Firefly", "Monster Part"],
        efecto: "Stealth Up",
        duracion: "varía — +1:30 por ingrediente", 
      },
      {
        nombre: "Chilly Elixir",
        ingredientes: ["Cold Darner", "Monster Part"],
        efecto: "Heat Resistance",
        duracion: "≈4 minutos sumando bonus", 
      },
      // Más entradas...
    ];

    function buscar() {
      const ing = document.getElementById("ingrediente").value.toLowerCase();
      const ef = document.getElementById("efecto").value;
      const tbody = document.querySelector("#tabla tbody");
      tbody.innerHTML = "";

      recetas.filter(r => {
        return (ing === "" || r.ingredientes.some(i => i.toLowerCase().includes(ing)))
            && (ef === "" || r.efecto === ef);
      }).forEach(r => {
        const tr = document.createElement("tr");
        tr.innerHTML = `<td>${r.nombre}</td>
                        <td>${r.ingredientes.join(", ")}</td>
                        <td>${r.efecto}</td>
                        <td>${r.duracion}</td>`;
        tbody.appendChild(tr);
      });
    }
  </script>
</body>
</html>
