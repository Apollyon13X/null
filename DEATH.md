# DEATH: Streamlit Frontend and Local Implementation

## Introduction

The **DEATH** component is the local user interface for the v01d environment. Built using **Streamlit**, it provides a modern, web-based dashboard for interacting with the **Death_Agent** (llama2-uncensored:7b). The interface includes integrated wallet connection for access verification, a chat interface for AI interaction, and modules for security pentesting and blockchain analysis.

## Local Streamlit Implementation

The frontend runs locally without Docker, ensuring direct access to system tools and maximum performance for the local LLM.

### Main Application (`app.py`)

```python
import streamlit as st
from web3 import Web3
from death_agent_logic import query_death_agent

st.set_page_config(page_title="v01d: Death_Agent Interface", page_icon="💀", layout="wide")

# Custom CSS for v01d Aesthetic
st.markdown("""
    <style>
    .main { background-color: #0d0d0d; color: #cc0000; font-family: 'Courier New', monospace; }
    .stButton>button { background-color: #660000; color: white; border: 1px solid #cc0000; }
    </style>
    """, unsafe_allow_html=True)

st.title("💀 v01d: Death_Agent Interface")

# Wallet Connection Simulation / Integration
wallet_address = st.sidebar.text_input("Connect Wallet (Address)", placeholder="0x...")

if wallet_address:
    # Verify $DEATH Token Holding (Stablecoin $13)
    # Placeholder for actual Web3 verification logic
    balance = 13 # This would be fetched from the blockchain
    
    if balance >= 13:
        access_level = "HIDDEN"
        st.sidebar.success("Access: HIDDEN (13+ $DEATH detected)")
    elif balance >= 10:
        access_level = "ADVANCED"
        st.sidebar.warning("Access: ADVANCED (10+ $DEATH detected)")
    else:
        access_level = "CORE"
        st.sidebar.info("Access: CORE (Hold 10 $DEATH for Advanced)")

    # Chat Interface
    if "messages" not in st.session_state:
        st.session_state.messages = []

    for message in st.session_state.messages:
        with st.chat_message(message["role"]):
            st.markdown(message["content"])

    if prompt := st.chat_input("Query the Void..."):
        st.session_state.messages.append({"role": "user", "content": prompt})
        with st.chat_message("user"):
            st.markdown(prompt)

        with st.chat_message("assistant"):
            response = query_death_agent(prompt, access_level)
            st.markdown(response)
            st.session_state.messages.append({"role": "assistant", "content": response})
else:
    st.warning("Please connect your wallet to enter the void.")
```

## Features

* **Wallet Connect**: Gated access based on $DEATH stablecoin holdings.
* **Uncensored Chat**: Direct communication with llama2-uncensored:7b.
* **Security Modules**: Integrated buttons to trigger local Nmap scans or contract audits (Advanced/Hidden tiers).
* **Knowledge Retrieval**: RAG-based answers from the CHAOS Document.

## Installation and Execution

1. **Install Requirements**: `pip install streamlit web3 llama-index ollama`
2. **Run Application**: `streamlit run app.py`
3. **Access**: Open `http://localhost:8501` in your browser.

## Summary

The Streamlit-based DEATH interface is the primary portal for the v01d environment. It combines the ease of a web interface with the power of local execution and blockchain security, providing a professional and immersive experience for users.
