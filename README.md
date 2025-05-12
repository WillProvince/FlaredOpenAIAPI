# FlareOpenAI-API-Adapter  
**A lightweight API adapter for Cloudflare Workers AI to OpenAI-compatible clients**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)  
*Facilitating seamless integration between Cloudflare's AI infrastructure and OpenAI-compatible applications*

---

## Overview  
This API adapter provides compatibility between Cloudflare Workers AI and clients designed for the OpenAI API specification. Originally developed and tested with Nextcloud Assistant, the solution enables integration with various applications that support OpenAI-style API endpoints.

---

## Key Features  
- **API Translation Layer**: Real-time translation between Cloudflare Workers AI and OpenAI API specifications  
- **Cross-Platform Compatibility**: Verified with Nextcloud Assistant (probably supports other OpenAI-compatible clients)  
- **Lightweight Deployment**: Single-instance service with minimal resource requirements  
- **Secure Configuration**: Environment-based credential management

---

## Installation & Configuration  

### Prerequisites  
- Python 3.9+  
- Cloudflare Workers AI access credentials  
- OpenAI-compatible client application  

### Deployment Procedure  
1. **Download Release Package**  
   Obtain the latest release from the [Releases page](https://github.com/WillProvince/FlaredOpenAIAPI/releases) and extract contents.

2. **Configure Service**  
   ```bash
   # Edit configuration file
   nano config.py
   ```
   Replace placeholder values with your Cloudflare credentials:  
   ```python
   ACCOUNT_ID = "your_cloudflare_account_id"  # Keep quotes for string value
   ```

3. **Launch Service**  
   ```bash
   python main.py
   ```

---

## Nextcloud Integration  
1. Install **OpenAI & LocalAI Integration** app via Nextcloud Marketplace  
2. Navigate to:  
   `Nextcloud Administration → Artificial Intelligence Settings`  
3. Configure endpoint:  
   - **API Endpoint**: `http://[server-ip]:[port]` (e.g., `http://192.168.88.94:5050`)  
   - **API Key**: Your Cloudflare Workers AI authorization token  

---

## Usage Verification  
Validate installation by sending a test request through your OpenAI-compatible client. For direct API verification:

```bash
curl -X POST http://localhost:5050/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model": "@cf/meta/llama-2-7b-chat-int8", "messages": [{"role": "user", "content": "Hello"}]}'
```

---

## License  
Distributed under MIT License. See `LICENSE` for full text.

---

**Compatibility Note**: While primarily tested with Nextcloud Assistant, this adapter should function with any OpenAI API-compatible client. Results may vary based on specific client requirements.
