# **Deploy the Researchly research abstract classifier**
Researchly predicts whether a research abstract belongs to the artificial intelligence or classical research category. Question 1 established the text-cleaning rules and logistic regression baseline. Question 2 selected the final classifier: TF–IDF word and word-pair features, supervised term weighting, and a linear support vector machine (SVM).
Run the classifier on Windows
1. Right-click Researchly-Project.zip, choose Extract All, and open the extracted researchly folder.
2. Open deployment and double-click index.html. If Windows asks which app to use, choose Edge, Chrome or Firefox.
3. Leave the sample abstract in the text box and click Classify Abstract. Under Prediction, the neural-network example should return artificial intelligence.
4. Replace the sample with another research abstract and click Classify Abstract again.
The browser runs the trained model bundled inside index.html. This option works offline and needs no Python installation, API key or dataset upload.
Serve the app over local HTTP
If you want a local web address, open PowerShell in the extracted researchly folder that contains deployment and requirements.txt. With Python installed, run:
python -m http.server 8000 --bind 127.0.0.1 --directory deployment
Open the local classifier and perform the sample test above. Keep PowerShell open during testing. Press Ctrl+C to stop the server. If the page shows a 404, run Test-Path .\deployment\index.html in PowerShell. The command should return True when you are in the correct folder.
Deploy online
Upload deployment/index.html as the root index.html of a static website. If the host deploys directly from this repository, choose deployment as the publish directory and leave the build command empty. Open the resulting URL and repeat the sample test.

Open the private hosted Question 2 classifier. Use the offline steps above if you do not have access to the private site.
Rebuild after changing the model
1. From the repository root, run python -m pip install -r requirements.txt, then python -m jupyter lab.
2. Open ITNPAQuestion2.ipynb. Keep data/research_abstracts.json in place and run the notebook from the first cell through the final export cell.
3. Find the generated Researchly-Classifier.html in the notebook's working directory. Copy it into deployment as index.html, replacing the previous model.
4. Repeat the sample test and publish the updated file.
If using the Google Colab / Gradio demonstration
Run the model setup cell and the Gradio interface cell in the same Colab session. The setup cell creates clean_text and the fitted pipeline best. If the interface reports either object is missing after a runtime restart, rerun the setup cell first. Open the share URL printed by app.launch(share=True) and keep the runtime active while testing.
