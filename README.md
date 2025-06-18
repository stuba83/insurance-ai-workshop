# Azure AI Foundry Workshop: Intelligent Claims Risk Assessment Agent

## 🌟 Workshop Title:
**"Empowering Insurance with AI Agents: Real-Time Intelligence with Azure AI Foundry"**

## 🕒 Duration:
**3 hours**

## 🎯 Workshop Objective:
To demonstrate how Azure AI Foundry can be used to build intelligent agents that enhance decision-making in the insurance industry using Retrieval-Augmented Generation (RAG) and real-time data via Bing Search.

## 🧠 Use Case:
### **"Intelligent Claims Risk Assessment Agent"**

This agent helps insurance adjusters assess the risk level of a new claim by:
- Retrieving internal policy and claims data (RAG)
- Searching for real-time external data (e.g., news about natural disasters, fraud alerts) using Bing Search
- Providing a summarized risk score and justification

## 🧰 Tools & Technologies:
- **Azure AI Foundry Studio (GUI-based)**
- **Azure AI Foundry AI Agents**
- **Azure OpenAI (GPT + RAG)**
- **Azure AI Search (formerly Cognitive Search)**
- **Bing Search API**
- **Sample insurance documents** (policies, claims history)

## ✅ Prerequisites:
Before the workshop, ensure you have:
- An active **Azure subscription**
- Access to **Azure AI Foundry Studio**
- **Azure OpenAI resource** with GPT-4 deployment
- **Azure AI Search** service
- **Bing Search v7 API key** from Azure Marketplace
- Azure Portal access

## 🏗️ Architecture Overview

```
User Query → AI Agent → [RAG Tool + Bing Search Tool] → Risk Assessment Output
                ↓
        ┌─────────────────┐    ┌─────────────────┐
        │   Internal      │    │   External      │
        │   Data (RAG)    │    │   Data (Bing)   │
        │   - Policies    │    │   - News        │
        │   - Claims      │    │   - Weather     │
        │   - History     │    │   - Fraud Alerts│
        └─────────────────┘    └─────────────────┘
```

## ☁️ Azure Setup Instructions (Step-by-Step)

### 1. Create Resource Group
1. Go to the [Azure Portal](https://portal.azure.com/)
2. Click **Create a resource** → **Resource group**
3. Fill in details:
   - **Subscription**: Your subscription
   - **Resource group**: `AI-Foundry-Insurance-Workshop`
   - **Region**: `East US` (recommended)
4. Click **Review + create** → **Create**

### 2. Create Azure AI Foundry Hub
1. In Azure Portal, search for **Azure AI Foundry**
2. Click **Create** → **AI Foundry hub**
3. Configure:
   - **Subscription**: Your subscription
   - **Resource group**: `AI-Foundry-Insurance-Workshop`
   - **Name**: `insurance-workshop-hub`
   - **Region**: `East US`
4. Click **Review + create** → **Create**

⏱️ **Wait time**: 5-10 minutes

### 3. Create Azure OpenAI Resource
1. In Azure Portal, create **Azure OpenAI** resource
2. Configuration:
   - **Name**: `openai-insurance-workshop`
   - **Resource group**: `AI-Foundry-Insurance-Workshop`
   - **Region**: `East US`
   - **Pricing tier**: Standard S0
3. After creation, go to **Model deployments**
4. Deploy **gpt-4o** model:
   - **Deployment name**: `gpt-4o-mini`
   - **Model version**: Latest
   - **Deployment type**: Standard

### 4. Create Azure AI Search
1. Create **Azure AI Search** service
2. Configuration:
   - **Service name**: `insurance-search-service`
   - **Resource group**: `AI-Foundry-Insurance-Workshop`
   - **Location**: `East US`
   - **Pricing tier**: Basic
3. Note the **Search service URL** and **Admin key**

### 5. Create Bing Search API
1. Go to Azure Marketplace
2. Search for **Bing Search v7**
3. Create resource:
   - **Name**: `bing-search-insurance`
   - **Resource group**: `AI-Foundry-Insurance-Workshop`
   - **Pricing tier**: Free tier (1,000 calls/month)
4. Copy the **API key** from Keys and Endpoint

## 🛠️ Step-by-Step Guide: Build the AI Agent

### 🔹 Step 1: Access Azure AI Foundry Studio
1. Go to [Azure AI Studio](https://ai.azure.com/)
2. Sign in with your Azure account
3. Select your hub: `insurance-workshop-ai-foundry`
4. Click **+ New project**
5. Create project:
   - **Project name**: `Insurance-Risk-Assessment+lastname`
   - **Description**: `AI agent for assessing insurance claim risks`

### 🔹 Step 2: Upload Sample Data
1. In your project, go to **Data** → **+ Add data**
2. Choose **Upload files**
3. Upload the provided `insurance_policies_claims.txt`
4. Configure data source:
   - **Data source name**: `insurance-data`
   - **Description**: `Sample insurance policies and claims data`

### 🔹 Step 3: Create Search Index
1. Go to **Indexes** → **+ New index**
2. Select your uploaded data source
3. Configure index:
   - **Index name**: `insurance-claims-index`
   - **Vector settings**: Enable for semantic search
   - **Embedding model**: Use text-embedding-ada-002
4. Review field mappings and click **Create**

⏱️ **Processing time**: 5-15 minutes depending on data size

### 🔹 Step 4: Create AI Agent
1. Go to **Agents** → **+ Create agent**
2. Configure basic settings:
   - **Agent name**: `Insurance Risk Assessor`
   - **Description**: `AI agent that assesses insurance claim risks using internal data and real-time external information`
   - **Instructions**: 
   ```
   You are an expert insurance risk assessor. Your role is to evaluate insurance claims by:
   1. Analyzing internal policy and claims data
   2. Gathering relevant external information (news, weather, fraud alerts)
   3. Providing a risk assessment with justification
   
   Always provide:
   - Risk Level: LOW, MEDIUM, or HIGH
   - Confidence Score: 1-10
   - Key Risk Factors found
   - Recommendations for next steps
   ```

### 🔹 Step 5: Configure Agent Tools

#### Add RAG Tool (Internal Data):
1. In your agent, click **+ Add Knowledge base**
2. Select **Upload Files**
3. Configure:
   - **Vector Store name**: `insurance-vector-store`

#### Add Bing Search Tool (External Data):
1. Click **+ Add tool** again
2. Select **Bing Search**
3. Configure:
   - **Connection name**: `bing-search-connection`
   - **API key**: Your Bing Search API key
   - **Description**: `Search for real-time external information like news, weather, and fraud alerts`

### 🔹 Step 6: Configure Model Settings
1. In agent settings, configure:
   - **Model**: `gpt-4o` (your deployment)
   - **Temperature**: `0.3` (for consistent responses)
   - **Max tokens**: `1000`
   - **System message**: Use the instructions from Step 4

### 🔹 Step 7: Test the Agent
1. Click **Test** in the agent interface
2. Try this sample query:
   ```
   A new flood claim was submitted by policy holder John Doe in Kingston, Jamaica. 
   Policy ID: POL001. Please assess the risk level.
   ```

Expected agent behavior:
- Search internal data for John Doe's history
- Search Bing for recent flood events in Kingston
- Provide risk assessment with justification

## 🚀 Demo Scenarios

### Scenario 1: High-Risk Flood Claim
**Input**: 
```
New flood claim submitted by Sarah Johnson in Miami, Florida. 
Policy ID: POL015. Claim amount: $50,000. Assess risk.
```

**Expected Output**:
```
RISK ASSESSMENT RESULTS

Risk Level: HIGH
Confidence Score: 8/10

Key Risk Factors:
• Customer has 2 previous flood claims in past 18 months
• Miami recently experienced Hurricane Ian flooding (external data)
• Claim amount significantly higher than previous claims
• Location in known flood-prone area

Recommendations:
• Require immediate adjuster inspection
• Verify damages with photos/documentation
• Check for recent flood insurance policy changes
• Cross-reference with weather service flood reports
```

### Scenario 2: Low-Risk Auto Claim
**Input**:
```
Minor auto accident claim by Michael Brown. 
Policy ID: POL008. Claim amount: $2,500. Assess risk.
```

### Scenario 3: Fraud Alert Scenario
**Input**:
```
Fire damage claim by Jennifer Davis. 
Policy ID: POL022. Claim amount: $75,000. Recent policy increase. Assess risk.
```

## 📊 Workshop Results

By the end of this workshop, you will have:
- ✅ A fully functional AI Agent in Azure AI Foundry
- ✅ RAG implementation using internal insurance data
- ✅ Real-time external data integration via Bing Search
- ✅ Automated risk assessment with justification
- ✅ Understanding of AI Agent orchestration

## 🔧 Troubleshooting Common Issues

### Issue: "Model deployment not found"
**Solution**: Ensure your OpenAI model is properly deployed and the deployment name matches your agent configuration.

### Issue: "Search index not accessible"
**Solution**: Verify your AI Search service permissions and ensure the index is fully processed.

### Issue: "Bing Search API calls failing"
**Solution**: Check your API key and ensure you haven't exceeded the free tier limits.

### Issue: "Agent responses are inconsistent"
**Solution**: Lower the temperature setting and refine your system instructions.

## 🚀 Next Steps & Extensions

After completing the workshop, consider:

1. **Enhanced Data Sources**: Add more insurance data types (property records, credit scores, etc.)
2. **Multi-modal Capabilities**: Include image analysis for damage assessment
3. **Integration with CRM**: Connect to existing insurance systems
4. **Custom Actions**: Add automated workflows (email alerts, case assignment)
5. **Advanced Analytics**: Implement performance tracking and model monitoring

## 📦 Workshop Resources

### Files Included:
- `insurance_policies_claims.csv` - Sample dataset (500 records)
- `workshop_slides.pptx` - Presentation materials
- `architecture_diagram.png` - Visual system overview
- `test_scenarios.json` - Additional test cases

### Useful Links:
- [Azure AI Foundry Documentation](https://docs.microsoft.com/azure/ai-foundry/)
- [AI Agents Best Practices](https://docs.microsoft.com/azure/ai-foundry/agents/)
- [Bing Search API Reference](https://docs.microsoft.com/bing/search-apis/)

## 💰 Cost Estimation

**Workshop Duration**: 3 hours
**Estimated Cost**: $15-25 USD

**Cost Breakdown**:
- Azure OpenAI (GPT-4o): ~$10-15
- Azure AI Search: ~$2-5
- Bing Search API: Free tier
- Azure AI Foundry: Included in consumption

## 🙋‍♀️ Support & Feedback

For questions during the workshop:
1. Check the troubleshooting section above
2. Consult Azure AI Foundry documentation
3. Open a GitHub issue in this repository
4. Contact the workshop facilitator

---

**Ready to build intelligent insurance agents? Let's get started! 🚀**