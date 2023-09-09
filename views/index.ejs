(async function () {
  // Dependencies
  const express = require("express");
  const app = express();
  const fs = require("fs");
  const multer = require("multer");
  const { createWorker } = require("tesseract.js");

  const worker = await createWorker({
    logger: (m) => {
      console.log(m.progress);
    },
  });

  // config the storage
  const storage = multer.diskStorage({
    destination: (req, file, cb) => {
      cb(null, "./uploads");
    },
    filename: (req, file, cb) => {
      cb(null, file.originalname);
    },
  });
  const upload = multer({ storage: storage }).single("avatar");

  // set the UI
  app.set("view engine", "ejs");
  app.use(express.static("public"));

  // routes //
  app.get("/", (req, res) => {
    res.render("index");
  });

  // uploading the file here
  app.post("/upload", (req, res) => {
    upload(req, res, (error) => {
      console.log(req.file);
      // reading the uploaded file here
      fs.readFile(`./uploads/${req.file.originalname}`, (error, data) => {
        (async () => {
          await worker.loadLanguage("eng");
          await worker.initialize("eng");
          const {
            data: { text, pdf },
          } = await worker.recognize(
            data,
            { pdfTitle: "Example PDF" },
            { pdf: true }
          );
          // process data here
          fs.writeFileSync("./output/tesseract-ocr-result.pdf", Buffer.from(pdf));
          console.log("Generate PDF: tesseract-ocr-result.pdf");
          await worker.terminate();
          res.redirect("/download");
        })();
      });
    });
  });

  app.get("/download", (req, res) => {
    const file = `${__dirname}/output/tesseract-ocr-result.pdf`;
    res.download(file);
  });

  const PORT = 5000 || process.env.PORT;
  app.listen(PORT, () =>
    console.log(`Everything running well on port: ${PORT}`)
  );
})();
