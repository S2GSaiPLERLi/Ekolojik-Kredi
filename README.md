ekolojik-kredi/
├── backend/               # Backend klasörü
│   ├── app.py             # Flask uygulaması
│   ├── requirements.txt   # Python bağımlılıkları
├── frontend/              # Frontend klasörü
│   ├── index.html         # Ana sayfa
│   ├── style.css          # CSS dosyası
│   ├── script.js          # JavaScript dosyası
├── README.md              # Proje açıklaması
├── .gitignore             # Git için göz ardı edilecek dosyalar
from flask import Flask, jsonify, request

app = Flask(__name__)

# Örnek atık verisi
waste_data = [
    {"date": "2024-12-01", "amount": 100},
    {"date": "2024-12-02", "amount": 150}
]

@app.route('/wastes', methods=['GET'])
def get_waste_data():
    return jsonify(waste_data)

@app.route('/wastes', methods=['POST'])
def add_waste():
    new_waste = request.json
    waste_data.append(new_waste)
    return jsonify({"message": "Atık verisi eklendi!"}), 201

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
    flask
    pip install -r requirements.txt
    <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ekolojik Kredi Sistemi</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>Ekolojik Kredi Sistemi</h1>

    <h2>Günlük Atık Verisi</h2>
    <div id="wasteData"></div>

    <h3>Yeni Atık Ekle</h3>
    <form id="wasteForm">
        <label for="date">Tarih:</label><br>
        <input type="date" id="date" name="date" required><br><br>
        <label for="amount">Miktar (kg):</label><br>
        <input type="number" id="amount" name="amount" required><br><br>
        <button type="submit">Ekle</button>
    </form>

    <script src="script.js"></script>
</body>
</html>
