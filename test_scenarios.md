# Test Scenarios for Insurance Risk Assessment AI Agent

## 🧪 Testing Your AI Agent

Use these scenarios to test your AI Agent's capabilities after setup. Each scenario tests different aspects of the agent's ability to combine internal data (RAG) with external data (Bing Search).

## 📋 Test Scenario Categories

### 1. High-Risk Scenarios
### 2. Medium-Risk Scenarios  
### 3. Low-Risk Scenarios
### 4. Complex Multi-Factor Scenarios
### 5. Edge Cases

---

## 🔴 High-Risk Scenarios

### Scenario 1: Repeat Flood Claimant
**Input Query:**
```
A new flood claim has been submitted by John Doe for policy POL001 in Kingston, Jamaica. 
The claim amount is $30,000. Please assess the risk level.
```

**Expected Agent Behavior:**
- Search internal data: Find John Doe has 2 previous claims
- Search Bing: Recent flooding in Kingston, Jamaica
- Risk Level: HIGH
- Key factors: Repeat claimant + location flood risk

### Scenario 2: Suspicious Fire Claim
**Input Query:**
```
Jennifer Davis has submitted a fire claim for $120,000 under policy POL004 in Los Angeles. 
She claims electrical fault caused the house fire. Assess the risk.
```

**Expected Agent Behavior:**
- Search internal data: Recent policy increase, no previous claims
- Search Bing: Fire investigation techniques, electrical fire patterns
- Risk Level: HIGH
- Key factors: High amount + recent policy increase + fraud indicators

### Scenario 3: Hurricane Season Claim
**Input Query:**
```
Sarah Johnson filed a hurricane damage claim for $85,000 in Miami, Florida under policy POL002. 
The damage occurred during Hurricane Ian. Please evaluate the risk.
```

**Expected Agent Behavior:**
- Search internal data: 1 previous claim in hurricane zone
- Search Bing: Hurricane Ian damage reports in Miami
- Risk Level: HIGH (but legitimate)
- Key factors: Major weather event + high-risk location

---

## 🟡 Medium-Risk Scenarios

### Scenario 4: Auto Theft in High-Crime Area
**Input Query:**
```
Robert Wilson reported his vehicle stolen in Houston, Texas under policy POL005. 
Claim amount is $15,000. The vehicle was stolen from a parking garage. Assess risk.
```

**Expected Agent Behavior:**
- Search internal data: 1 previous claim, high crime area noted
- Search Bing: Recent auto theft rates in Houston
- Risk Level: MEDIUM
- Key factors: High crime location + previous claim history

### Scenario 5: Hit and Run Investigation
**Input Query:**
```
Kevin Johnson's parked car was damaged in a hit and run incident in Las Vegas under policy POL013. 
Claim amount $11,500. No witnesses available. Evaluate the risk.
```

**Expected Agent Behavior:**
- Search internal data: 1 previous claim, no witnesses
- Search Bing: Hit and run claim investigation procedures
- Risk Level: MEDIUM
- Key factors: No witnesses + previous claim + verification challenges

---

## 🟢 Low-Risk Scenarios

### Scenario 6: Minor Auto Collision
**Input Query:**
```
Michael Brown had a minor rear-end collision in Phoenix, Arizona under policy POL003. 
Claim amount is $4,500. He has a clean driving record. Assess the risk.
```

**Expected Agent Behavior:**
- Search internal data: Clean record, no previous claims
- Search Bing: Typical minor collision repair costs
- Risk Level: LOW
- Key factors: Clean record + reasonable claim amount

### Scenario 7: Natural Disaster with Documentation
**Input Query:**
```
Emily Chen's pipe burst in Seattle, Washington causing $18,000 in water damage under policy POL010. 
The building has old infrastructure. Evaluate risk.
```

**Expected Agent Behavior:**
- Search internal data: No previous claims, old building noted
- Search Bing: Pipe burst frequency in old buildings, Seattle weather
- Risk Level: LOW
- Key factors: First claim + documented infrastructure issue

---

## 🔄 Complex Multi-Factor Scenarios

### Scenario 8: Tornado Alley Property Claim
**Input Query:**
```
Michelle Taylor submitted a tornado damage claim for $95,000 in Oklahoma City under policy POL016. 
The damage occurred during tornado season. This is her first claim. Assess comprehensively.
```

**Expected Agent Behavior:**
- Search internal data: First claim, tornado alley location
- Search Bing: Recent tornado activity in Oklahoma City, typical damage costs
- Risk Level: MEDIUM-HIGH (legitimate but high exposure)
- Key factors: Geographic risk + seasonal timing + high amount but first claim

### Scenario 9: Multiple Environmental Factors
**Input Query:**
```
Heather Davis reported earthquake damage of $42,000 in Salt Lake City under policy POL026. 
The area recently experienced seismic activity. Evaluate all risk factors.
```

**Expected Agent Behavior:**
- Search internal data: No previous claims, seismic activity zone
- Search Bing: Recent earthquakes in Salt Lake City, typical damage patterns
- Risk Level: MEDIUM
- Key factors: Natural disaster + geographic risk + no previous claims

---

## ⚡ Edge Cases & Complex Queries

### Scenario 10: Ambiguous Claim Information
**Input Query:**
```
A customer with policy POL999 (not in our database) submitted a claim. 
How should this be handled and what risk factors should be considered?
```

**Expected Agent Behavior:**
- Search internal data: Policy not found
- Search Bing: Insurance claim verification procedures
- Response: Request policy verification + standard risk assessment protocols

### Scenario 11: Multi-State Weather Event
**Input Query:**
```
We have multiple claims coming in from the same weather event affecting Texas, Louisiana, and Mississippi. 
How should we assess risks for these related claims?
```

**Expected Agent Behavior:**
- Search internal data: Multiple policies in affected states
- Search Bing: Multi-state weather event details, CAT event classification
- Response: Catastrophic event procedures + batch processing recommendations

### Scenario 12: Timing Inconsistencies
**Input Query:**
```
A claim was submitted for damage that allegedly occurred 6 months ago but is just being reported now. 
Policy POL015 in Kansas City. What additional risk factors should be considered?
```

**Expected Agent Behavior:**
- Search internal data: Delayed reporting history
- Search Bing: Late claim reporting regulations and red flags
- Risk Level: MEDIUM-HIGH
- Key factors: Delayed reporting + investigation requirements

---

## 📊 Expected Response Format

Each agent response should include:

```
RISK ASSESSMENT RESULTS
======================

Policy Information:
• Policy ID: [ID]
• Customer: [Name]
• Location: [City, State/Country]
• Policy Type: [Type]

Risk Level: [LOW/MEDIUM/HIGH]
Confidence Score: [1-10]/10

Internal Data Findings:
• [Key finding 1]
• [Key finding 2]
• [Key finding 3]

External Data Findings:
• [External factor 1]
• [External factor 2]
• [External factor 3]

Key Risk Factors:
• [Risk factor 1 with severity]
• [Risk factor 2 with severity]
• [Risk factor 3 with severity]

Recommended Actions:
1. [Action 1]
2. [Action 2]
3. [Action 3]

Additional Investigation Needed:
• [Investigation point 1]
• [Investigation point 2]
```

---

## 🎯 Testing Checklist

After running these scenarios, verify your agent can:

- ✅ Successfully retrieve internal policy/claims data
- ✅ Execute external Bing searches for relevant information
- ✅ Combine internal and external data for analysis
- ✅ Assign appropriate risk levels with justification
- ✅ Provide actionable recommendations
- ✅ Handle edge cases gracefully
- ✅ Maintain consistent response format
- ✅ Show appropriate confidence levels

## 🔧 Troubleshooting Test Results

**If tests fail, check:**

1. **Data Retrieval Issues**:
   - Search index is properly configured
   - Field mappings are correct
   - Permissions are set correctly

2. **External Search Issues**:
   - Bing Search API key is valid
   - API quotas not exceeded
   - Search queries are well-formed

3. **Response Quality Issues**:
   - Adjust model temperature (try 0.1-0.5)
   - Refine system instructions
   - Add more specific examples in prompts

4. **Inconsistent Results**:
   - Check for randomness in model settings
   - Verify data consistency in search index
   - Review agent instructions for clarity

---

**Ready to test your AI Agent? Start with Scenario 1 and work your way through! 🚀**