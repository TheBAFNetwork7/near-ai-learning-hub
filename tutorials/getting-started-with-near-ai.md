# Getting Started with NEAR AI: A Step-by-Step Guide to Setting Up and Running Your First Agent

NEAR AI allows developers to create AI-powered agents that interact, execute tasks, and integrate with decentralized environments on the NEAR Protocol. The NEAR AI CLI (Command Line Interface) provides the tools needed to develop, test, and deploy these agents efficiently.

This guide will walk you through:

✅  Setting up your development environment

✅  Installing NEAR AI CLI

✅  Creating and configuring your first AI agent

✅  Understanding the NEAR Wallet for authentication

✅  Running the agent interactively

📢 By the end, you’ll have a functional AI agent running locally, ready for further development.

## 1. Prerequisites
Before starting, ensure you have:

1. 🖥 macOS or Linux (Windows users should use WSL2 or a VM)
2. 🐍 Python 3.9 - 3.11 (NEAR AI does not support Python 3.12+ yet)
3. 🔄 Git installed
4. 🔑 A NEAR Wallet (Create one here)

> **📝 Why is a NEAR Wallet needed?**
> 
> NEAR AI agents interact with the NEAR blockchain, and the wallet is required to authenticate transactions, store credentials, and deploy AI agents.

## 2. Understanding the NEAR AI CLI
The NEAR AI CLI is a command-line tool that allows developers to:
- Create AI agents
- Run agents interactively
- Inspect and modify agent logic
- Deploy agents to the NEAR AI Registry
  
Think of it as a terminal-based interface for efficiently managing NEAR AI agents.

## 3. Setting Up Your Development Environment
### **3.1 Check & Install Homebrew (If Not Installed)**

First, check if **Homebrew** is already installed:

```
which brew
```

If the output is empty, install Homebrew (**otherwise, skip this step**):

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, update your system:

```
brew update
```
---
### **3.2 Install Python (Recommended: 3.11)**

First, check your Python version:

```
python3 --version
```

If you see **Python 3.9 - 3.11**, you're good to go! **If not, install Python 3.11**:

```
brew install python@3.11
```

Verify the installation:

```
python3 --version
```
---
### **3.3 Set Up a Virtual Environment**

To **isolate dependencies** and avoid conflicts, create a **virtual environment**:

```
cd ~
python3.11 -m venv nearai-env
source nearai-env/bin/activate
```

Confirm the virtual environment is active:

```
which python3
```

If everything is correct, you should see:

```
/Users/your_username/nearai-env/bin/python3
```

## **4. Installing NEAR AI**

Now, install **NEAR AI CLI**:

```
pip install --upgrade pip setuptools
pip install nearai
```

Verify the installation:

```
python3 -m nearai version
```

Expected output (example):
```
0.1.13
```

## **5. Connecting Your NEAR Wallet**

Before creating an agent, you need to **log in** to your NEAR Wallet:

```
nearai login
```

This will open a browser window asking you to **approve the authentication request** with your wallet.

> Why is this necessary?
> 
> Your NEAR account is used to **store credentials** and **deploy AI agents** to the blockchain.
> 


## **6. Creating Your First AI Agent**

Now that **NEAR AI is installed and authenticated**, let’s create an **AI agent**.

Navigate to your working directory:

```
cd ~
```

Create an agent:

```
nearai agent create --name "my_first_agent"
```

Expected output:

```
🎉 SUCCESS!
New AI Agent created at: /Users/your_username/.nearai/registry/your_wallet.near/my_first_agent/0.0.1
```

---

## 7. Understanding Agent Files

Your agent folder contains:

📄 **`agent.py`** – The core logic of your AI agent

This file defines how your agent **processes inputs**, **responds to queries**, and **executes actions**. You can customize it to add new behaviors.

📄 **`metadata.json`** – The agent’s metadata

This file contains **metadata** such as the agent's **name, version, description**, and dependencies.

Navigate to your agent directory:

```
cd ~/.nearai/registry/your_wallet.near/my_first_agent/0.0.1
```

List files:

```
ls -la
```

Open and edit the agent’s code:

```
nano agent.py
```

## **8. Running Your Agent Locally**

To start an **interactive session** with your agent:

```
nearai agent interactive ~/.nearai/registry/your_wallet.near/my_first_agent/0.0.1 --local
```

Expected output:

```
=== Starting interactive session with agent: your_wallet.near/my_first_agent/0.0.1 ===
Type 'exit' to end the session
>
```

Try interacting with the agent:

```
> Hello
```

To exit the session:

```
exit
```

or press **Ctrl + C**.

---

## **9. Troubleshooting & Lessons Learned**

### **Common Issues & Fixes**

| **Issue** | **Solution** |
| --- | --- |
| `failed to enable ddtrace support for requests` | Install `ddtrace` manually: `pip install ddtrace==2.21.0` |
| `ModuleNotFoundError: No module named 'openai'` | Install `openai`: `pip install openai` |
| `Agent not found` | Ensure you are running the command from the correct directory |
| `Python 3.13+ not supported` | Use Python 3.11 (`brew install python@3.11`) and create a new virtual environment |
| `Login issues with NEAR Wallet` | Try `nearai logout` and `nearai login` again |
| `error: command 'gcc-11' failed: No such file or directory` | **Solution:** <br> - Install gcc-11: `sudo apt update && sudo apt install gcc-11` <br> - OR create a symlink: `sudo ln -s $(which gcc) /usr/bin/gcc-11` <br> - OR set the compiler variable: `export CC=gcc` before installing nearai |


---

## **10. Next Steps**

🎉 **Congratulations!** You have successfully:

✅ Installed NEAR AI

✅ Logged in with your NEAR Wallet

✅ Created and ran an AI agent

✅ Debugged common issues

### **What’s Next?**

📌 Modify `agent.py` to customize your AI logic

📌 Deploy your agent on the **NEAR AI Registry**

📌 Explore **multi-agent communication**

For further reading, check the [NEAR AI Documentation](https://docs.near.ai/)
