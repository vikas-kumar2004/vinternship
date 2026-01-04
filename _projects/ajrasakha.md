---
layout: project
title: Ajrasakha
order: 5
summary: AI-powered agricultural advisory platform with expert knowledge base and multi-level review system
color: "059669"
repo: "vicharanashala/ajrasakha"
features: []
---

## **Project Overview**

Ajrasakha connects farmers with verified agricultural knowledge through an AI-powered chat interface. The system uses a Golden Dataset of verified Q&As and Package of Practices (PoP), leveraging vector search and semantic similarity for accurate answers. When AI can't help, questions route to agricultural experts for review. The platform features multi-level moderation with expert performance tracking, reputation scores, and continuous learning where verified answers feed back into the Golden Dataset.

## **Key Features**

Farmers interact through an AI chat interface that provides state and crop-specific answers in multiple regional languages. They can track their questions in real-time as they move through the review system. The Golden Dataset uses MongoDB Atlas vector search with HuggingFace embeddings (BAAI/bge-large-en-v1.5) for semantic search, automatically growing as approved expert answers get added back.

When AI can't answer, questions route to agricultural specialists whose responses go through moderator review. The system tracks expert performance using reputation scores, incentives, and penalties. The analytics dashboard monitors dataset growth, expert contributions, question status distribution, moderator approval rates, and question sources.

## **Technologies Used**

The backend uses TypeScript, Express.js, Node.js, MongoDB Atlas with Vector Search, InversifyJS for dependency injection, Firebase Authentication, and Sentry for error monitoring. The frontend is built with React, TypeScript, TanStack Router, TanStack Query, Shadcn UI, and Tailwind CSS.

For AI/ML, the platform uses DeepSeek-R1 (70B), Qwen3 (1.7B), and GPT-OSS (20B) LLMs via Ollama, HuggingFace BAAI/bge-large-en-v1.5 for embeddings, MongoDB Atlas as the vector database, and MCP servers for structured data access. Additional services include MCP tools for Golden Dataset and FAQ access, audio processing for voice queries, and Sarvam AI API for regional languages.

## **System Architecture**

When farmers submit questions, the system detects context (state and crop information) and searches the Golden Dataset using vector search. If no match exists, it searches the Package of Practices database. Still no answer? The question routes to agricultural experts who provide responses with metadata. Moderators review and approve the best answer, which gets added to the Golden Dataset. The farmer receives a notification when their answer is ready.

The platform serves four user types: Farmers (submit questions, receive answers), Experts (answer routed questions, earn reputation), Moderators (review and approve expert answers), and Admins (system management).

## **Data Structure**

The Golden Dataset stores question-answer pairs with embeddings, metadata (state, crop, season, domain, specialist, sources), similarity scores, and verification status. Expert performance tracking includes reputation scores, incentive tracking, penalty tracking, and response quality metrics.

## **Project Goals**

Ajrasakha provides instant agricultural guidance using AI while building a comprehensive knowledge base that grows smarter over time. The platform connects farmers with experts for complex queries, implements multi-level quality control, and tracks expert contributions through incentives. It delivers state and crop-specific advice in regional languages, creating a self-improving knowledge base that helps identify common agricultural challenges.

## **GitHub Repository**

[Ajrasakha](https://github.com/{{ page.repo }}){:target="_blank"}

{% if page.features.size > 0 %}
## **Upcoming Features**

{% for feature in page.features %}
<details style="margin-bottom: 1.5rem; border-radius: 12px; overflow: hidden; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
<summary style="cursor: pointer; padding: 1rem 1.5rem; background: linear-gradient(135deg, #{{ page.color }}20 0%, #{{ page.color }}40 100%); border-left: 6px solid #{{ page.color }}; font-weight: 600; list-style: none;">&nbsp;{{ feature.title }}</summary>
<div style="padding: 1.5rem; background-color: white;">
{{ feature.description }}
<br><br>
<a href="https://github.com/{{ page.repo }}/issues/{{ feature.issue }}" target="_blank" style="color: #{{ page.color }}; font-weight: 600; text-decoration: none;">View Feature Request #{{ feature.issue }} →</a>
</div>
</details>
{% endfor %}
{% endif %}
