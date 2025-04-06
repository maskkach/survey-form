# survey-form
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>Document</title>
    <style>
    body {
        background-color: #ffe6f0; /* світло-рожевий фон */
        font-family: 'Segoe UI', 'Helvetica Neue', sans-serif; /* шрифт без засічок */
        color: #333;
        margin: 20;
        padding: 0;
    }

    header, main, footer {
        max-width: 600px;
        margin: auto;
        padding: 10px;
    }

    header h2, main h1 {
        text-align: center;
        color: #cc3366;
    }

    form {
        background-color: #fff;
        border-radius: 20px;
        padding: 40px;
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    }

    fieldset {
        border: none;
        padding: 10;
    }

    legend {
        font-size: 1.5em;
        margin-bottom: 15px;
        color: #cc3366;
    }

    label, p {
        display: block;
        margin: 15px 10 5px;
    }

    input, select, textarea, button {
        width: 100%;
        padding: 15px;
        border: 1px solid #ddd;
        border-radius: 8px;
        font-size: 1em;
        box-sizing: border-box;
    }

    input[type="checkbox"],
    input[type="radio"] {
        width: auto;
        margin-right: 10px;
    }

    textarea {
        resize: vertical;
    }

    button, input[type="submit"] {
        background-color: #ff80ab;
        color: white;
        border: none;
        cursor: pointer;
        margin-top: 20px;
        transition: background-color 0.3s ease;
    }

    button:hover, input[type="submit"]:hover {
        background-color: #e64a8b;
    }

    hr {
        margin: 25px 0;
        border: none;
        height: 1px;
        background-color: #eee;
    }
</style>
</head>

<body>
    <header>
        <h2>Опитування</h2>
    </header>

    <main>
      
        <article>
            <div>
                <form id="telegram-form">
                    <fieldset>
                        <legend></legend>

                        <label>
                            <p>Ім'я і прізвисько (наприклад Машка ромашка)</p>
                            <input id="firstName" name="Ім'я і прізвисько" type="text" required minlength="4" maxlength="100"
                                placeholder="Ім'я й прізвисько">
                        </label><br>

                        <p>Номер телефону (у форматі 380.........)</p>
                        <input type="Номер телефону" name="Номер" min="0" max="400000000000" required  placeholder="вони і так у мене всі є 😈"><br>

                        <p>Email</p>
                        <input type="email" name="Email"><br>

                        <p>Улюблений колір</p>
                        <input type="color" name="Улюблений колір"><br>

                        <p>ДН</p>
                        <input type="date" name="ДН"><br>
                    
                        <p>Я не Саша Коваль</p>
                        <input type="checkbox" name="Я не Саша Коваль" required><br>

                        <header>
                        <p><h2>Поооооїхали</h2></p>
                        </header>

                        <p>Якби вибули парканом, то яким</p>
                        <label><input type="radio" name="Якби вибули парканом, то яким" value="Синім"> Синім</label><br>
                        <label><input type="radio" name="Якби вибули парканом, то яким" value="Зеленим"> Зеленим</label><br>
                        <label><input type="radio" name="Якби вибули парканом, то яким" value="Іржавим"> Іржавим</label><br>

                        <p>Яким би сміттєвим баком ви б хотіли бути</p>
                        <label><input type="radio" name="Яким би сміттєвим баком ви б хотіли бути?" value="Великим"> Великим</label><br>
                        <label><input type="radio" name="Яким би сміттєвим баком ви б хотіли бути?" value="Маленьким"> Маленьким</label><br>
                        <label><input type="radio" name="Яким би сміттєвим баком ви б хотіли бути?" value="Домашнім"> Домашнім</label><br>
                    
                        <p>Чим пахне дно моря?</p>
                        <textarea id="Чим пахне дно моря?" name="Чим пахне дно моря?" rows="5" cols="33"></textarea><br>

                        <p>Шоколадка</p>
                        <select name="Шоколадка">
                            <option value="Twix">Twix</option>
                            <option value="Bounty" selected>Bounty</option>
                            <option value="Snickers">Snickers</option>
                        </select><br><br>

                        <button type="submit">Надіслати</button>
                    </fieldset>
                </form>
            </div>
        </article>
    </main>

    <footer></footer>

    <script>
        document.getElementById("telegram-form").addEventListener("submit", function (e) {
            e.preventDefault();

            const formData = new FormData(this);
            let message = "📝 *Нова форма відправлена:*\n\n";

            for (const [key, value] of formData.entries()) {
                message += `*${key}*: ${value}\n`;
            }

            const token = "7904667365:AAG7Obdprlp9x78LnQ2hZMZgyici1m4tf18"; // Встав свій токен сюди
            const chatId = "@chebotaievaandkifa"; // Твій канал

            fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({
                    chat_id: chatId,
                    text: message,
                    parse_mode: "Markdown"
                })
            })
            .then(response => response.json())
            .then(data => {
                alert("Повідомлення надіслано в Telegram!");
            })
            .catch(error => {
                alert("Сталася помилка при надсиланні.");
                console.error("Telegram error:", error);
            });
        });
    </script>
</body>
</html>
