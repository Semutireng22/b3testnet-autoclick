# Auto Click B3 Testnet

## Cara Penggunaan

### Langkah 1: Buka Halaman Web

Buka halaman 

### Langkah 2: Buka Developer Tools

1. Klik kanan pada halaman web dan pilih "Inspect" atau tekan `Ctrl+Shift+I` (Windows/Linux) atau `Cmd+Option+I` (Mac) dan jika menggunakan hp gunakanlah mises browser atau kiwi browser masuk ke `Developers Tools`
2. Pergi ke tab "Console".

### Langkah 3: Salin dan Tempel Script

Salin script di bawah ini dan tempelkan ke konsol, lalu tekan Enter.

```javascript
(function() {
    // Create the popup HTML
    const popupHtml = `
        <div id="autoClickerPopup" style="position: fixed; top: 50px; right: 50px; width: 250px; padding: 15px; background-color: white; border: 1px solid #ccc; border-radius: 10px; z-index: 10000; font-family: Arial, sans-serif; box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);">
            <h3 style="margin: 0 0 10px; font-size: 16px; text-align: center; color: #333;">Auto Clicker</h3>
            <label for="clickCount" style="display: block; margin-bottom: 5px; font-size: 14px; color: #333;">Jumlah Klik:</label>
            <input type="number" id="clickCount" min="1" value="10" style="width: 100%; padding: 5px; box-sizing: border-box; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 4px;">
            <label for="clickInterval" style="display: block; margin-bottom: 5px; font-size: 14px; color: #333;">Interval (ms):</label>
            <input type="number" id="clickInterval" min="1" value="1000" style="width: 100%; padding: 5px; box-sizing: border-box; margin-bottom: 10px; border: 1px solid #ccc; border-radius: 4px;">
            <small style="display: block; margin-bottom: 10px; color: #666; text-align: center;">Minimal 1 ms</small>
            <button id="startAutoClicker" style="width: 100%; padding: 10px; background-color: #28a745; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 14px;">Mulai</button>
            <button id="stopAutoClicker" style="width: 100%; padding: 10px; background-color: #dc3545; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 14px; margin-top: 5px;">Berhenti</button>
            <button id="closePopup" style="width: 100%; padding: 10px; background-color: #6c757d; color: white; border: none; border-radius: 4px; cursor: pointer; font-size: 14px; margin-top: 5px;">Tutup</button>
            <p style="text-align: center; color: #666; font-size: 12px; margin-top: 15px;">Channel: <a href="https://t.me/ugdairdrop" target="_blank" style="color: #007bff; text-decoration: none;">t.me/ugdairdrop</a></p>
        </div>
    `;

    // Append the popup to the body
    document.body.insertAdjacentHTML('beforeend', popupHtml);

    // Function to get element by XPath
    function getElementByXpath(path) {
        return document.evaluate(path, document, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null).singleNodeValue;
    }

    // Initialize variables
    let autoClickerInterval;

    // Start button click event
    document.getElementById('startAutoClicker').addEventListener('click', function() {
        const clickCount = parseInt(document.getElementById('clickCount').value);
        const clickInterval = parseInt(document.getElementById('clickInterval').value);
        let clicks = 0;

        // Validate input
        if (isNaN(clickCount) || clickCount <= 0) {
            alert('Jumlah klik harus lebih besar dari 0.');
            return;
        }
        if (isNaN(clickInterval) || clickInterval < 1) {
            alert('Interval harus minimal 1 ms.');
            return;
        }

        // Clear any existing interval
        clearInterval(autoClickerInterval);

        // XPath selector for the canvas element
        const xpathSelector = "//html/body/div/main/div[1]/div[1]/div[1]/canvas";

        // Start the auto clicker
        autoClickerInterval = setInterval(() => {
            if (clicks < clickCount) {
                // Find the canvas element using XPath and trigger a click event
                const elementToClick = getElementByXpath(xpathSelector);
                if (elementToClick) {
                    console.log('Element ditemukan, mengklik...');
                    // Create a new MouseEvent
                    const clickEvent = new MouseEvent('click', {
                        view: window,
                        bubbles: true,
                        cancelable: true
                    });
                    elementToClick.dispatchEvent(clickEvent);
                    console.log(`Klik ke-${clicks + 1} berhasil`);
                    clicks++;
                } else {
                    console.error('Element tidak ditemukan.');
                    clearInterval(autoClickerInterval);
                }
            } else {
                clearInterval(autoClickerInterval);
                console.log('Auto click selesai.');
            }
        }, clickInterval);
    });

    // Stop button click event
    document.getElementById('stopAutoClicker').addEventListener('click', function() {
        clearInterval(autoClickerInterval);
        console.log('Auto click dihentikan.');
    });

    // Close button click event
    document.getElementById('closePopup').addEventListener('click', function() {
        document.getElementById('autoClickerPopup').remove();
    });
})();
```

### Langkah 4: Menggunakan Auto Clicker

1. **Mengatur Jumlah Klik dan Interval**:
   - Setelah menempelkan script, sebuah popup akan muncul di sudut kanan atas layar.
   - Atur jumlah klik yang diinginkan di input "Jumlah Klik".
   - Atur interval waktu antara setiap klik dalam milidetik di input "Interval (ms)".

2. **Mulai Auto Clicker**:
   - Klik tombol "Mulai" untuk memulai auto clicker.
   - Script akan mulai berjalan sesuai dengan jumlah klik dan interval yang telah diatur.

3. **Menghentikan Auto Clicker**:
   - Klik tombol "Berhenti" untuk menghentikan auto clicker sebelum jumlah klik yang diinginkan tercapai.

4. **Menutup Popup**:
   - Klik tombol "Tutup" untuk menutup popup.

### Catatan
- Script ini baru eksperimen belum tentu bekerja dengan baik.
- Jika terdapat error silahkan hubungi saya

### Channel
Untuk informasi lebih lanjut dan pembaruan, kunjungi channel Telegram kami: [t.me/ugdairdrop](https://t.me/ugdairdrop)
