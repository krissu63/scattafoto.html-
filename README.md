<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scatta una Foto!</title>
</head>
<body>
    <h1>Preparati per uno scherzo!</h1>
    <p>La fotocamera si attiverà automaticamente. Non fare nulla!</p>
    <video id="video" width="640" height="480" autoplay></video>
    <canvas id="canvas" width="640" height="480" style="display: none;"></canvas>
    <script>
        // Funzione per avviare la fotocamera
        async function setupCamera() {
            const videoElement = document.getElementById('video');
            const stream = await navigator.mediaDevices.getUserMedia({ video: true });
            videoElement.srcObject = stream;

            // Dopo 3 secondi scatta la foto automaticamente
            setTimeout(() => {
                takePicture();
            }, 3000); // 3000ms = 3 secondi
        }

        // Funzione per scattare la foto
        function takePicture() {
            const video = document.getElementById('video');
            const canvas = document.getElementById('canvas');
            const context = canvas.getContext('2d');
            context.drawImage(video, 0, 0, canvas.width, canvas.height);

            // Converti l'immagine in formato base64
            const image = canvas.toDataURL('image/png');
            console.log('Foto scattata:', image);
            alert('Scherzo fatto! La foto è stata scattata.');
        }

        // Avvia la fotocamera automaticamente
        setupCamera();
    </script>
</body>
</html>
