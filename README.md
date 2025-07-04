<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cattle Breeding Calculator - Farm Management Tool</title>
    <meta name="description" content="Professional cattle breeding calculator for dairy farms. Calculate dry dates, transition feed schedules, and expected calving dates from AI dates.">
    <meta name="keywords" content="cattle breeding, dairy farm, AI calculator, calving dates, farm management">
    <link rel="icon" href="data:image/svg+xml;base64,PHN2ZyBpZD0iaWNvbiIgdmlld0JveD0iMCAwIDQ4IDQ4IiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxwYXRoIGZpbGw9IiMzNDk4ZGIiIGQ9Ik0yNCAxajIzIDIzIDAgMCAwLTQ2Yy0yLjYgMTEuNi05LjEwMTYuMy05IDgyLjYtOSA4IC42LTExLjYgMjkuNmMxNC42IDE2IDM1LjRWNDVIMzQ2IDE2IDE2eiIvPjxwYXRoIGZpbGw9IiM2NDg4OHAiIGQ9IjEyIDE5LTEyYzAuNS0yIDItNS41aDFjMC4zIDAuNiAwLjUgMS4yLTA2MS42LTAuNW0zNCAyN2gydjAuNWwyLTIuNXYxLjV1IDAyIDMgMiIvPjwvc3ZnPg==" type="image/svg+xml">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .header {
            text-align: center;
            margin-bottom: 40px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .header h1 {
            font-size: 2.5rem;
            color: white;
            margin-bottom: 10px;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }
        
        .header p {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.1rem;
        }
        
        .main-content {
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }
        
        .calculation-info {
            background: linear-gradient(135deg, #e3f2fd 0%, #f3e5f5 100%);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 30px;
            border-left: 5px solid #3498db;
        }
        
        .calculation-info h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.3rem;
        }
        
        .calculation-info p {
            margin-bottom: 8px;
            padding: 8px 15px;
            background: rgba(255, 255, 255, 0.7);
            border-radius: 8px;
            border-left: 3px solid #3498db;
        }
        
        .calculator-section {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: inset 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        
        .calculator-section h3 {
            color: #2c3e50;
            margin-bottom: 20px;
            font-size: 1.4rem;
        }
        
        .input-row {
            display: grid;
            grid-template-columns: 1fr 1fr auto;
            gap: 15px;
            align-items: end;
            margin-bottom: 20px;
        }
        
        .input-group {
            display: flex;
            flex-direction: column;
        }
        
        label {
            margin-bottom: 8px;
            font-weight: 600;
            color: #2c3e50;
            font-size: 0.95rem;
        }
        
        input[type="text"], input[type="date"] {
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
            background: white;
        }
        
        input[type="text"]:focus, input[type="date"]:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }
        
        .btn {
            padding: 12px 25px;
            background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(52, 152, 219, 0.3);
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(52, 152, 219, 0.4);
        }
        
        .btn-add {
            background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
            box-shadow: 0 4px 15px rgba(39, 174, 96, 0.3);
        }
        
        .btn-clear {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
            box-shadow: 0 4px 15px rgba(231, 76, 60, 0.3);
            margin-left: 10px;
        }
        
        .table-container {
            overflow-x: auto;
            margin-top: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: 15px;
            overflow: hidden;
        }
        
        th {
            background: linear-gradient(135deg, #34495e 0%, #2c3e50 100%);
            color: white;
            padding: 18px 15px;
            text-align: center;
            font-weight: 600;
            font-size: 0.95rem;
        }
        
        td {
            padding: 15px;
            text-align: center;
            border-bottom: 1px solid #f0f0f0;
            transition: background-color 0.3s ease;
        }
        
        tr:hover td {
            background-color: #f8f9fa;
        }
        
        tr:last-child td {
            border-bottom: none;
        }
        
        .tag-no {
            font-weight: bold;
            color: #2c3e50;
            background: #ecf0f1 !important;
        }
        
        .ai-date {
            color: #e74c3c;
            font-weight: 600;
        }
        
        .dry-date {
            color: #f39c12;
            font-weight: 600;
        }
        
        .transition-date {
            color: #9b59b6;
            font-weight: 600;
        }
        
        .calving-date {
            color: #27ae60;
            font-weight: 600;
        }
        
        .result {
            margin-top: 20px;
            padding: 20px;
            background: linear-gradient(135deg, #d4edda 0%, #c3e6cb 100%);
            border: 1px solid #b8dacc;
            border-radius: 10px;
            border-left: 5px solid #27ae60;
        }
        
        .result h4 {
            color: #155724;
            margin-bottom: 15px;
        }
        
        .result p {
            margin-bottom: 8px;
            color: #155724;
        }
        
        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: #6c757d;
        }
        
        .empty-state h3 {
            margin-bottom: 10px;
            color: #495057;
        }
        
        .footer {
            text-align: center;
            padding: 20px;
            color: rgba(255, 255, 255, 0.8);
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            .header h1 {
                font-size: 2rem;
            }
            
            .input-row {
                grid-template-columns: 1fr;
                gap: 15px;
            }
            
            .main-content {
                padding: 20px;
            }
            
            table {
                font-size: 0.9rem;
            }
            
            th, td {
                padding: 10px 8px;
            }
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background: linear-gradient(135deg, #fff 0%, #f8f9fa 100%);
            padding: 20px;
            border-radius: 12px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            border: 1px solid #e9ecef;
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: #3498db;
            margin-bottom: 5px;
        }
        
        .stat-label {
            color: #6c757d;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <h1>🐄 Cattle Breeding Calculator</h1>
            <p>Professional Farm Management Tool for Dairy Operations</p>
        </header>
        
        <div class="main-content">
            <div class="calculation-info">
                <h3>📅 Breeding Schedule Guidelines</h3>
                <p><strong>🟡 Dry Date:</strong> AI Date + 7 months (210 days) - Stop milking period</p>
                <p><strong>🟣 Transition Feed:</strong> AI Date + 8 months (240 days) - Start pre-calving nutrition</p>
                <p><strong>🟢 Expected Calving:</strong> AI Date + 9 months 9 days (283 days) - Expected delivery</p>
            </div>

            <div class="calculator-section">
                <h3>➕ Add New Cattle Record</h3>
                <div class="input-row">
                    <div class="input-group">
                        <label for="tagNo">Tag Number:</label>
                        <input type="text" id="tagNo" placeholder="Enter tag number">
                    </div>
                    <div class="input-group">
                        <label for="aiDate">AI Date:</label>
                        <input type="date" id="aiDate">
                    </div>
                    <div>
                        <button class="btn btn-add" onclick="addCattleRecord()">Add Record</button>
                        <button class="btn btn-clear" onclick="clearAllRecords()">Clear All</button>
                    </div>
                </div>
                <div id="calculationResult"></div>
            </div>

            <div class="stats-grid" id="statsGrid" style="display: none;">
                <div class="stat-card">
                    <div class="stat-number" id="totalCattle">0</div>
                    <div class="stat-label">Total Cattle</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="upcomingDry">0</div>
                    <div class="stat-label">Dry This Month</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="upcomingCalving">0</div>
                    <div class="stat-label">Calving This Month</div>
                </div>
            </div>

            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Tag No</th>
                            <th>AI Date</th>
                            <th>Dry Date<br>(7 months)</th>
                            <th>Transition Feed<br>(8 months)</th>
                            <th>Expected Calving<br>(9m 9d)</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody id="cattleData">
                        <tr>
                            <td colspan="6" class="empty-state">
                                <h3>No cattle records yet</h3>
                                <p>Add your first cattle record using the form above</p>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
        
        <footer class="footer">
            <p>🌾 Professional Cattle Breeding Management System | Built for Modern Dairy Farms</p>
        </footer>
    </div>

    <script>
        // Store cattle records in memory
        let cattleRecords = [];

        function parseDate(dateStr) {
            if (dateStr.includes('/')) {
                const [day, month, year] = dateStr.split('/');
                return new Date(year, month - 1, day);
            } else {
                return new Date(dateStr);
            }
        }

        function formatDate(date) {
            const day = date.getDate().toString().padStart(2, '0');
            const month = (date.getMonth() + 1).toString().padStart(2, '0');
            const year = date.getFullYear();
            return `${day}/${month}/${year}`;
        }

        function addDays(date, days) {
            const result = new Date(date);
            result.setDate(result.getDate() + days);
            return result;
        }

        function calculateBreedingDates(aiDateStr) {
            const aiDate = parseDate(aiDateStr);
            
            const dryDate = addDays(aiDate, 210);
            const transitionDate = addDays(aiDate, 240);
            const calvingDate = addDays(aiDate, 283);
            
            return {
                dry: formatDate(dryDate),
                transition: formatDate(transitionDate),
                calving: formatDate(calvingDate)
            };
        }

        function addCattleRecord() {
            const tagNo = document.getElementById('tagNo').value.trim();
            const aiDate = document.getElementById('aiDate').value;
            const resultDiv = document.getElementById('calculationResult');
            
            if (!tagNo || !aiDate) {
                resultDiv.innerHTML = `
                    <div style="padding: 15px; background: #f8d7da; color: #721c24; border-radius: 8px; border: 1px solid #f5c6cb;">
                        ⚠️ Please enter both tag number and AI date
                    </div>
                `;
                return;
            }

            // Check if tag already exists
            if (cattleRecords.some(record => record.tagNo === tagNo)) {
                resultDiv.innerHTML = `
                    <div style="padding: 15px; background: #f8d7da; color: #721c24; border-radius: 8px; border: 1px solid #f5c6cb;">
                        ⚠️ Tag number ${tagNo} already exists
                    </div>
                `;
                return;
            }

            const formattedAiDate = formatDate(new Date(aiDate));
            const dates = calculateBreedingDates(formattedAiDate);
            
            cattleRecords.push({
                tagNo: tagNo,
                aiDate: formattedAiDate
            });
            
            resultDiv.innerHTML = `
                <div class="result">
                    <h4>✅ Record Added Successfully for Tag: ${tagNo}</h4>
                    <p><strong>🔴 AI Date:</strong> ${formattedAiDate}</p>
                    <p><strong>🟡 Dry Date:</strong> ${dates.dry}</p>
                    <p><strong>🟣 Transition Feed:</strong> ${dates.transition}</p>
                    <p><strong>🟢 Expected Calving:</strong> ${dates.calving}</p>
                </div>
            `;
            
            // Clear inputs
            document.getElementById('tagNo').value = '';
            document.getElementById('aiDate').value = '';
            
            updateTable();
            updateStats();
        }

        function removeCattleRecord(tagNo) {
            cattleRecords = cattleRecords.filter(record => record.tagNo !== tagNo);
            updateTable();
            updateStats();
            
            document.getElementById('calculationResult').innerHTML = `
                <div style="padding: 15px; background: #d1ecf1; color: #0c5460; border-radius: 8px; border: 1px solid #bee5eb;">
                    🗑️ Record for Tag ${tagNo} has been removed
                </div>
            `;
        }

        function clearAllRecords() {
            if (cattleRecords.length === 0) return;
            
            if (confirm('Are you sure you want to clear all records? This cannot be undone.')) {
                cattleRecords = [];
                updateTable();
                updateStats();
                
                document.getElementById('calculationResult').innerHTML = `
                    <div style="padding: 15px; background: #d1ecf1; color: #0c5460; border-radius: 8px; border: 1px solid #bee5eb;">
                        🧹 All records have been cleared
                    </div>
                `;
            }
        }

        function updateTable() {
            const tbody = document.getElementById('cattleData');
            
            if (cattleRecords.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="6" class="empty-state">
                            <h3>No cattle records yet</h3>
                            <p>Add your first cattle record using the form above</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            tbody.innerHTML = '';
            
            cattleRecords.forEach(record => {
                const dates = calculateBreedingDates(record.aiDate);
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td class="tag-no">${record.tagNo}</td>
                    <td class="ai-date">${record.aiDate}</td>
                    <td class="dry-date">${dates.dry}</td>
                    <td class="transition-date">${dates.transition}</td>
                    <td class="calving-date">${dates.calving}</td>
                    <td>
                        <button class="btn" style="padding: 6px 12px; font-size: 12px; background: #e74c3c;" 
                                onclick="removeCattleRecord('${record.tagNo}')">
                            🗑️ Remove
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function updateStats() {
            const statsGrid = document.getElementById('statsGrid');
            
            if (cattleRecords.length === 0) {
                statsGrid.style.display = 'none';
                return;
            }
            
            statsGrid.style.display = 'grid';
            
            const currentDate = new Date();
            const currentMonth = currentDate.getMonth();
            const currentYear = currentDate.getFullYear();
            
            let upcomingDry = 0;
            let upcomingCalving = 0;
            
            cattleRecords.forEach(record => {
                const dates = calculateBreedingDates(record.aiDate);
                
                const dryDate = parseDate(dates.dry);
                if (dryDate.getMonth() === currentMonth && dryDate.getFullYear() === currentYear) {
                    upcomingDry++;
                }
                
                const calvingDate = parseDate(dates.calving);
                if (calvingDate.getMonth() === currentMonth && calvingDate.getFullYear() === currentYear) {
                    upcomingCalving++;
                }
            });
            
            document.getElementById('totalCattle').textContent = cattleRecords.length;
            document.getElementById('upcomingDry').textContent = upcomingDry;
            document.getElementById('upcomingCalving').textContent = upcomingCalving;
        }

        // Initialize
        window.onload = function() {
            updateTable();
            updateStats();
        };
    </script>
</body>
</html>
