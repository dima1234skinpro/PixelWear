# PixelWear
тут ви зможете скачать скини
<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <title>BrighSkins – Скіни Minecraft</title>
  <link rel="stylesheet" href="style.css">
  <script src="skinview3d.min.js"></script>
</head>
<body>
  <h1>🎮 BrighSkins – Завантажуй свої скіни!</h1>
  
  <input type="file" id="skinUpload" accept=".png">
  <button id="downloadBtn">⬇️ Завантажити скін</button>

  <div id="viewer"></div>

  <script>
    const viewer = new skinview3d.SkinViewer({
      canvas: document.getElementById("viewer"),
      width: 300,
      height: 400,
      skin: "https://textures.minecraft.net/texture/7d03cb3eaa3c01206c5b40c90f882ef91f95bb74626c276eb0044a2dbcd7b1" // Заміни або залиш
    });
    viewer.controls.enableZoom = true;
    viewer.animation = new skinview3d.WalkingAnimation();
    viewer.animation.speed = 1;
    viewer.animation.play();

    document.getElementById("skinUpload").addEventListener("change", function () {
      const file = this.files[0];
      if (file && file.type === "image/png") {
        const reader = new FileReader();
        reader.onload = function (e) {
          viewer.loadSkin(e.target.result);
        };
        reader.readAsDataURL(file);
      } else {
        alert("Будь ласка, вибери PNG-файл.");
      }
    });

    document.getElementById("downloadBtn").addEventListener("click", () => {
      const link = document.createElement("a");
      link.href = viewer.skin.src;
      link.download = "minecraft_skin.png";
      link.click();
    });
  </script>
</body>
</html>
