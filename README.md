Setup Guide – Oak & Barrel AI Customer Support Agent
📌 Overview
This guide walks you through setting up the Flowise-powered Oak & Barrel Customer Support Agent using Google Generative AI and Pinecone Vector Database.
By the end of this setup, you’ll have:
•	A fully working chatbot embedded in the Oak & Barrel restaurant website.
•	A semantic search-enabled FAQ system.
•	A menu-based query assistant.
________________________________________
1. Prerequisites
Make sure you have:
•	Node.js ≥ 18.x
•	npm ≥ 9.x
•	Pinecone API Key
•	Google AI Studio API Key (Gemini API)
•	Flowise installed globally
Install Flowise:
npm install -g flowise
________________________________________
2. Clone the Repository
git clone https://github.com/yourusername/oak-barrel-support-agent.git
cd oak-barrel-support-agent
________________________________________
3. Start Flowise
flowise start
Open Flowise in your browser at:
http://localhost:3000
________________________________________
4. Create Chatbot Flow in Flowise
Follow the chatbot structure shown below:
Chatbot Flow Diagram
Main Components:
•	Google Generative AI Node
o	Model: gemini-pro (or latest available)
o	API Key: from Google AI Studio
•	Pinecone Vector Store Node
o	Index Name: flowise
o	API Key: from Pinecone
o	Environment: e.g., us-east1-gcp
•	Document Loader Nodes for:
o	menu.csv (menu items)
o	oak-and-barrel-qa.docx (FAQs)
________________________________________
5. Configure Pinecone
1.	Go to Pinecone Console.
2.	Create a new index (flowise) with:
o	Dimension: 768 (for text-embedding-004)
o	Metric: cosine
3.	Add your Pinecone API Key and environment to the Flowise Pinecone Node.
Example Config
________________________________________
6. Upload Documents
•	menu.csv → contains structured menu data.
•	oak-and-barrel-qa.docx → contains FAQ responses.
•	These will be converted to embeddings and stored in Pinecone.
________________________________________
7. Embed Chatbot in Oak & Barrel Website
In oak and barrel.html, add the Flowise embed script:
<script type="module">
import Chatbot from "https://cdn.jsdelivr.net/npm/flowise-embed/dist/web.js"
Chatbot.init({
    chatflowid: "YOUR_CHATFLOW_ID",
    apiHost: "http://localhost:3000",
})
</script>
________________________________________
8. Test the Chatbot
Open oak and barrel.html in your browser and interact with the chatbot.

