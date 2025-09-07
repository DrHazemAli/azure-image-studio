# Getting Started with Azure Image Studio

Welcome to Azure Image Studio! This guide will help you get up and running with our comprehensive AI-powered image generation and editing platform.

> ⚠️ **Important**: This is a **community project** and is not affiliated with or endorsed by Microsoft or Azure. It's an independent project that uses Azure AI services.

## 🚀 Quick Overview

Azure Image Studio is a community-developed, production-ready platform that integrates with Azure AI services to provide professional-grade image generation and editing capabilities. This independent project offers both a simple generation interface and a full-featured studio environment for advanced image manipulation.

**Note**: This is not an official Microsoft or Azure product, but rather a community project that utilizes Azure's AI services.

### Current Active Features

The platform currently supports comprehensive image generation and editing capabilities:

- **🎨 Image Generation**: Create images from text descriptions using various AI models
- **✏️ Image Editing**: Modify and enhance existing images with AI-powered tools
- **🖼️ Canvas Tools**: Professional editing tools including crop, resize, filters, shapes, and text
- **📁 Asset Management**: Built-in asset library with IndexedDB storage
- **📚 History Tracking**: Complete generation and editing history
- **🖥️ Real-time Console**: API request/response logging and debugging

## 📋 Prerequisites

Before you begin, ensure you have:

- **Node.js 18+** installed on your system
- **Azure subscription** with access to AI services
- **Azure OpenAI Service** account (for DALL-E 3 and GPT-Image-1 models)
- **Azure AI Foundry** access (for FLUX models)

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/DrHazemAli/azure-image-studio.git
cd azure-image-studio
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Azure Services

The platform uses a flexible configuration system that supports multiple Azure endpoints and models.

#### Environment Variables

Create a `.env.local` file in the root directory:

```bash
# Azure API Key (used for all models)
AZURE_API_KEY=your_azure_api_key_here
```

#### Model Configuration

Edit the configuration files in `src/app/config/`:

**`azure-config.json`** - Main endpoint configuration:
```json
{
  "endpoints": [
    {
      "id": "primary",
      "name": "Primary Endpoint",
      "baseUrl": "https://your-openai-endpoint.openai.azure.com",
      "apiVersion": "2025-04-01-preview",
      "deployments": [
        {
          "id": "dalle-3",
          "name": "DALL-E 3",
          "deploymentName": "your-dalle-3-deployment",
          "maxSize": "1024x1024",
          "supportedFormats": ["png", "jpeg"],
          "description": "High-quality image generation with DALL-E 3"
        }
      ]
    }
  ]
}
```

**`azure-models.json`** - Detailed model specifications and capabilities:
```json
{
  "imageModels": {
    "generation": {
      "openai": [
        {
          "id": "dalle-3",
          "name": "DALL-E 3",
          "description": "High-quality image generation with natural and vivid styles",
          "provider": "Azure OpenAI",
          "apiVersion": "2024-10-21",
          "capabilities": ["text-to-image"],
          "supportedSizes": [
            { "size": "1024x1024", "label": "Square (1:1)", "aspect": "1:1" }
          ],
          "supportedFormats": ["png", "jpeg"],
          "styleOptions": ["natural", "vivid"],
          "qualityLevels": ["standard", "hd"],
          "maxImages": 1,
          "requiresApproval": false
        }
      ]
    }
  }
}
```

### 4. Start the Development Server

```bash
npm run dev
```

### 5. Open Your Browser

Navigate to [http://localhost:3000](http://localhost:3000)

## 🎨 Using the Platform

### Simple Generation Interface

1. **Visit the Home Page**: The main page provides a simple interface for quick image generation
2. **Enter Your Prompt**: Describe the image you want to create
3. **Select Model**: Choose from available AI models (DALL-E 3, FLUX 1.1 Pro, etc.)
4. **Configure Settings**: Adjust size, quality, and other parameters
5. **Generate**: Click the generate button and wait for your image

### Professional Studio

1. **Launch Studio**: Click "Launch Azure Image Studio" from the home page
2. **Choose Tools**: Use the toolbar to select generation or editing tools
3. **Generate Images**: Create new images with AI assistance
4. **Edit Images**: Modify existing images using AI-powered editing tools
5. **Manage Assets**: Use the assets panel to organize your work
6. **Track History**: View your generation and editing history

## 🔧 Configuration Details

### Supported Models

| Model | Provider | Capabilities | Status |
|-------|----------|--------------|--------|
| DALL-E 3 | Azure OpenAI | Text-to-image | ✅ Active |
| GPT-Image-1 | Azure OpenAI | Text-to-image, Editing, Inpainting | ⚠️ Requires Approval |
| FLUX 1.1 Pro | Azure AI Foundry | Text-to-image | ✅ Active |
| FLUX 1 Kontext Pro | Azure AI Foundry | Text-to-image, Image-to-image, Editing | ✅ Active |

### Endpoint Configuration

Each model requires its own endpoint configuration:

- **Azure OpenAI Models**: Use your Azure OpenAI service endpoint
- **FLUX Models**: Use Azure AI Foundry endpoint
- **API Versions**: Each model may require different API versions

### Environment Setup

The platform automatically detects available models based on your configuration. Ensure:

1. All required deployments are created in Azure
2. API keys have proper permissions
3. Endpoints are correctly configured
4. Models are enabled in the configuration

## 🚨 Troubleshooting

### Common Issues

**"Azure API key not configured"**
- Ensure `AZURE_API_KEY` is set in your `.env.local` file

**"Invalid Azure configuration"**
- Check that your endpoint URLs are correct
- Verify deployment names match your Azure configuration
- Ensure API versions are compatible

**"Model not available"**
- Check if the model is enabled in `azure-models.json`
- Verify the deployment exists in Azure
- Ensure you have access to the required Azure service

### Getting Help

- Check the [User Guide](User-Guide.md) for detailed usage instructions
- Review the [API Documentation](API-Documentation.md) for technical details
- See our [Architecture Guide](Architecture.md) for system design overview

## 🎯 Next Steps

1. **Explore the Studio**: Try the professional studio interface
2. **Test Different Models**: Experiment with various AI models
3. **Learn Advanced Features**: Check out the [User Guide](User-Guide.md)
4. **Customize Configuration**: Adjust settings for your specific needs

## 📚 Additional Resources

- [User Guide](User-Guide.md) - Detailed usage instructions
- [API Documentation](API-Documentation.md) - Technical reference
- [Architecture Guide](Architecture.md) - System design overview
- [CLI Documentation](../cli/README.md) - Command-line interface guide
- [CLI User Guide](../cli/docs/CLI-User-Guide.md) - Comprehensive CLI usage guide
- [CLI API Documentation](../cli/docs/CLI-API-Documentation.md) - CLI technical reference

---

**Ready to start creating?** Launch the studio and begin generating amazing images with AI!