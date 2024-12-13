# 04-12-2024
async function processAndSubmit() {
    try {
        const response = await fetch('https://kodaktor.ru/j/numbers');
        const data = await response.json();
        const sum = data.numbers.reduce((acc, num) => acc + num, 0);
        const resultString = `${sum} (kamentsev)`;
        const formResponse = await fetch(
            'https://docs.google.com/forms/d/e/1FAIpQLSeZyDJ_68Mj7io5vtjyNqul7ceNE1t5Z5KkkN7foqxbIcUsbg/formResponse',
            {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/x-www-form-urlencoded',
                },
                body: new URLSearchParams({
                    'entry.364005965': resultString,
                }),
            }
        );
    }
}
processAndSubmit();
