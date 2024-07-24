<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Checklist de Obras</title>
    <style>
        body { font-family: Arial, sans-serif; background-color: #f4f4f4; margin: 0; padding: 0; }
        .container { width: 80%; margin: auto; overflow: hidden; }
        #main-header { background-color: #333; color: #fff; padding-top: 30px; min-height: 70px; border-bottom: #0779e4 3px solid; }
        #main-header h1 { text-align: center; text-transform: uppercase; margin: 0; font-size: 24px; }
        #main { padding: 20px; background: #fff; margin-top: 20px; }
        .checklist { list-style: none; padding: 0; }
        .checklist-item { background: #f9f9f9; margin: 5px 0; padding: 10px; border: 1px solid #ddd; }
        .checklist-item.completed { text-decoration: line-through; }
        .button { background: #0779e4; color: #fff; padding: 10px; text-align: center; border: none; cursor: pointer; }
    </style>
</head>
<body>
    <header id="main-header">
        <div class="container">
            <h1>Checklist de Obras</h1>
        </div>
    </header>
    <section id="main" class="container">
        <ul class="checklist" id="checklist">
            <!-- Items do checklist serão adicionados aqui -->
        </ul>
        <input type="text" id="new-item" placeholder="Novo item...">
        <button class="button" onclick="addItem()">Adicionar Item</button>
    </section>
    <script>
        let checklist = [];

        function renderChecklist() {
            const checklistElement = document.getElementById('checklist');
            checklistElement.innerHTML = '';
            checklist.forEach((item, index) => {
                const itemElement = document.createElement('li');
                itemElement.className = checklist-item ${item.completed ? 'completed' : ''};
                itemElement.innerHTML = `
                    <input type="checkbox" ${item.completed ? 'checked' : ''} onclick="toggleComplete(${index})">
                    <span>${item.text}</span>
                    <button class="button" onclick="deleteItem(${index})">Excluir</button>
                `;
                checklistElement.appendChild(itemElement);
            });
        }

        function addItem() {
            const newItemText = document.getElementById('new-item').value;
            if (newItemText) {
                checklist.push({ text: newItemText, completed: false });
                document.getElementById('new-item').value = '';
                renderChecklist();
            }
        }

        function toggleComplete(index) {
            checklist[index].completed = !checklist[index].completed;
            renderChecklist();
        }

        function deleteItem(index) {
            checklist.splice(index, 1);
            renderChecklist();
        }

        renderChecklist();
    </script>
</body>
</html>
