<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestion de l'argent et des dépenses</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
        }
        th {
            background-color: #f2f2f2;
            text-align: center;
        }
        td {
            text-align: center;
        }
        .total {
            font-weight: bold;
        }
        .form-section {
            margin-bottom: 20px;
        }
        .form-section label, .form-section input, .form-section button {
            margin-right: 10px;
        }
    </style>
</head>
<body>

<h1>Gestion de l'argent et des dépenses</h1>

<!-- Formulaire pour ajouter des transactions -->
<div class="form-section">
    <label for="category">Catégorie :</label>
    <select id="category">
        <option value="revenus">Revenus</option>
        <option value="courses">Courses</option>
        <option value="essence">Essence</option>
        <option value="autres">Autres Dépenses</option>
    </select>

    <label for="description">Description :</label>
    <input type="text" id="description" placeholder="Description">

    <label for="amount">Montant (€) :</label>
    <input type="number" id="amount" placeholder="Montant">

    <button onclick="addTransaction()">Ajouter</button>
</div>

<!-- Tableau des Revenus -->
<h2>Revenus</h2>
<table>
    <thead>
        <tr>
            <th>Date</th>
            <th>Description</th>
            <th>Montant (€)</th>
        </tr>
    </thead>
    <tbody id="income-body">
        <!-- Les lignes seront ajoutées ici -->
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2" class="total">Total Revenus</td>
            <td id="total-income">0</td>
        </tr>
    </tfoot>
</table>

<!-- Tableau des Dépenses pour Courses -->
<h2>Courses</h2>
<table>
    <thead>
        <tr>
            <th>Date</th>
            <th>Description</th>
            <th>Montant (€)</th>
        </tr>
    </thead>
    <tbody id="groceries-body">
        <!-- Les lignes seront ajoutées ici -->
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2" class="total">Total Courses</td>
            <td id="total-groceries">0</td>
        </tr>
    </tfoot>
</table>

<!-- Tableau des Dépenses pour Essence -->
<h2>Essence</h2>
<table>
    <thead>
        <tr>
            <th>Date</th>
            <th>Description</th>
            <th>Montant (€)</th>
        </tr>
    </thead>
    <tbody id="fuel-body">
        <!-- Les lignes seront ajoutées ici -->
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2" class="total">Total Essence</td>
            <td id="total-fuel">0</td>
        </tr>
    </tfoot>
</table>

<!-- Tableau des Autres Dépenses -->
<h2>Autres Dépenses</h2>
<table>
    <thead>
        <tr>
            <th>Date</th>
            <th>Description</th>
            <th>Montant (€)</th>
        </tr>
    </thead>
    <tbody id="other-body">
        <!-- Les lignes seront ajoutées ici -->
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2" class="total">Total Autres Dépenses</td>
            <td id="total-other">0</td>
        </tr>
    </tfoot>
</table>

<!-- Solde final -->
<h2>Solde Final</h2>
<table>
    <tfoot>
        <tr>
            <td class="total">Solde Total (€)</td>
            <td id="final-balance">0</td>
        </tr>
    </tfoot>
</table>

<script>
    const revenues = [];
    const groceries = [];
    const fuels = [];
    const others = [];

    function addTransaction() {
        const category = document.getElementById('category').value;
        const description = document.getElementById('description').value;
        const amount = parseFloat(document.getElementById('amount').value);
        const date = new Date().toISOString().split('T')[0]; // Date du jour au format AAAA-MM-JJ

        if (description && !isNaN(amount)) {
            const transaction = { date, description, amount };

            switch (category) {
                case 'revenus':
                    revenues.push(transaction);
                    updateTable(revenues, 'income-body', 'total-income');
                    break;
                case 'courses':
                    groceries.push(transaction);
                    updateTable(groceries, 'groceries-body', 'total-groceries');
                    break;
                case 'essence':
                    fuels.push(transaction);
                    updateTable(fuels, 'fuel-body', 'total-fuel');
                    break;
                case 'autres':
                    others.push(transaction);
                    updateTable(others, 'other-body', 'total-other');
                    break;
            }

            updateFinalBalance();
        }
    }

    function updateTable(data, tbodyId, totalId) {
        const tbody = document.getElementById(tbodyId);
        tbody.innerHTML = ''; // Efface les lignes existantes
        let total = 0;

        data.forEach(item => {
            const row = document.createElement('tr');
            row.innerHTML = `
                <td>${item.date}</td>
                <td>${item.description}</td>
                <td>${item.amount.toFixed(2)}</td>
            `;
            tbody.appendChild(row);
            total += item.amount;
        });

        document.getElementById(totalId).textContent = total.toFixed(2);
        return total;
    }

    function updateFinalBalance() {
        const totalIncome = parseFloat(document.getElementById('total-income').textContent) || 0;
        const totalGroceries = parseFloat(document.getElementById('total-groceries').textContent) || 0;
        const totalFuel = parseFloat(document.getElementById('total-fuel').textContent) || 0;
        const totalOther = parseFloat(document.getElementById('total-other').textContent) || 0;

        const finalBalance = totalIncome - (totalGroceries + totalFuel + totalOther);
        document.getElementById('final-balance').textContent = finalBalance.toFixed(2);
    }
</script>

</body>
</html>
