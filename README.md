# NVIDIA-Generative-AI-Lab-Resources

**NVIDIA-Certified Associate: Generative AI LLMs (NCA-GENL) — Complete Hands-On Lab Suite**
This repository contains all 21 Python Jupyter Notebook (.ipynb) labs and interactive worksheets across Chapters 1–8 of the NVIDIA-Certified Associate: Generative AI LLMs (NCA-GENL) study guide and NCA-GENL_Lab_Plan.xlsx, organized into Chapter_01 through Chapter_08 folders.

Every notebook is designed to run out of the box:
•	Live NVIDIA NIM / GPU Mode: Connects directly to https://integrate.api.nvidia.com/v1 when NVIDIA_API_KEY (nvapi-...) is set and uses CUDA GPUs when available.
•	Offline / CPU Fallback Mode: Automatically falls back to deterministic local execution and realistic telemetry if NVIDIA_API_KEY or a local GPU is not present, so every code cell executes cleanly anywhere.

**Quick Start**
1.	Install Python dependencies:
pip install -r requirements.txt
2.	(Optional) Configure your free NVIDIA Developer Program API Key:
•	Sign in at https://build.nvidia.com and generate an API key (nvapi-...).
•	Set the environment variable before launching Jupyter:

**Windows PowerShell**
$env:NVIDIA_API_KEY="nvapi-your-key-here"
jupyter lab

**Directory Structure & Complete Lab Index (Chapters 1–8)**
Chapter Folder	Notebook Path	Lab Type	Primary Topics & Exam Blueprint Alignment

Chapter_01	Chapter_01/Lab_1-01_Set_Up_Your_Lab.ipynb	Hosted-API lab	NVIDIA Developer Program (build.nvidia.com), NVIDIA_API_KEY, OpenAI-compatible NIM SDK, ChatNVIDIA, nvidia-smi & PyTorch CUDA checks, Discriminative vs. Generative AI
Chapter_01	Chapter_01/Exercise_1-02_Study_Planner.ipynb	Worksheet	Official 5 NCA-GENL exam domains (30%/24%/22%/14%/10%), gap-weighted study hour allocator, 14-day schedule, Two-Pass exam pacing simulator

Chapter_02	Chapter_02/Lab_2-01_Train_a_Small_Network_and_Fix_Overfitting.ipynb	Notebook lab	PyTorch nn.Module, 5-step training loop, Cross-Entropy Loss, AdamW, diagnosing Overfitting (High Variance) vs. Underfitting (High Bias), Dropout, Weight Decay (L2), and Early Stopping
Chapter_02	Chapter_02/Lab_2-02_CPU_vs_GPU_Precision_and_Memory_Sizing.ipynb	Notebook lab (GPU)	CPU vs. GPU FP32 vs. GPU FP16 Tensor Core GEMM timing, FP16 overflow vs. BF16 exponent range, 7B/13B/70B VRAM sizing (FP32/FP16/INT8/INT4), KV Cache & 16 B/param AdamW training memory

Chapter_03	Chapter_03/Lab_3-01_Hugging_Face_Pipelines_and_Tokenizers.ipynb	Notebook lab	spaCy linguistic pipelines (Doc, Token, POS, dependency parsing, NER) vs. Hugging Face pipeline() (sentiment, NER, summarization, zero-shot), AutoTokenizer (input_ids, attention_mask), Python generators (yield)
Chapter_03	Chapter_03/Lab_3-02_RAG_Chatbot_on_NVIDIA_Endpoints.ipynb	Hosted-API lab	RecursiveCharacterTextSplitter (chunk_size, chunk_overlap), NVIDIAEmbeddings (nv-embedqa-e5-v5), FAISS, NVIDIARerank (nv-rerankqa-mistral-4b-v3), ChatNVIDIA with [doc-id] citations & out-of-scope abstention
Chapter_03	Chapter_03/Lab_3-03_Streaming_and_Latency.ipynb	Hosted-API lab	stream=True (SSE) vs. stream=False, Time to First Token (TTFT / Prefill), Inter-Token Latency (ITL / Decode), End-to-End Latency, and Throughput (tokens/sec)
Chapter_03	Chapter_03/Lab_3-04_Run_an_LLM_NIM_Container.ipynb	Local GPU lab	Docker & NVIDIA Container Toolkit (--gpus all, -e NGC_API_KEY, --shm-size=16GB, /opt/nim/.cache), /v1/health/ready, /v1/models, and local http://localhost:8000/v1 streaming benchmark

Chapter_04	Chapter_04/Lab_4-01_LoRA_Fine_Tuning_with_Experiment_Tracking.ipynb	Notebook lab (GPU)	Full Fine-Tuning vs. PEFT / LoRA ($W_0 + \frac{\alpha}{r}BA$) & QLoRA (NF4), Hugging Face peft (LoraConfig), rank/LR sweep with set_seed(42), MLflow tracking, and adapter weight merging
Chapter_04	Chapter_04/Lab_4-02_Evaluation_Metrics_and_LM_Evaluation_Harness.ipynb	Notebook lab	EleutherAI LM Evaluation Harness (lm-eval) (MMLU, HellaSwag, GSM8K, HumanEval), BLEU (translation precision + brevity penalty), ROUGE-1/2/L (summarization recall/F1), Perplexity, multi-seed confidence intervals
Chapter_04	Chapter_04/Exercise_4-03_Design_a_Controlled_Experiment.ipynb	Worksheet	Falsifiable vs. null hypotheses, independent/dependent/controlled/confounding variables, Random vs. Stratified vs. Time-Based vs. Group-Based splits, automated data leakage & $n$-gram contamination detector

Chapter_05	Chapter_05/Lab_5-01_Text_Dataset_EDA_CPU_vs_cudf_pandas.ipynb	Notebook lab (GPU)	Corpus profiling (nulls, empty strings, TTR), Mean vs. Median & P95/P99 token lengths for context window sizing, Zipf's Law (log-log plot), exact & near-duplicate removal, RAPIDS cudf.pandas (%load_ext cudf.pandas, %%cudf.pandas.profile)
Chapter_05	Chapter_05/Lab_5-02_Embedding_Visualization.ipynb	Notebook lab	L2-normalized text embeddings projected with PCA (explained variance ratio), t-SNE (varying perplexity), and UMAP (n_neighbors, min_dist), plus proving what 2D plots can and cannot prove vs. high-D Cosine Similarity

Chapter_06	Chapter_06/Lab_6-01_NeMo_Guardrails_with_a_Red_Team_Test.ipynb	Hosted-API lab	NVIDIA NeMo Guardrails (config.yml + Colang .co input, dialog, and output rails), 20-prompt Red-Team & benign test suite, Confusion Matrix (Wrongly Allowed / FN vs. Wrongly Blocked / FP Over-Refusals)
Chapter_06	Chapter_06/Lab_6-02_Bias_Probe_with_Counterfactual_Prompts.ipynb	Hosted-API lab	Sources of AI bias, Allocational vs. Representational harm, Counterfactual Prompt Probes across names/pronouns, Agentic vs. Communal tone & length analysis, Disaggregated Subgroup Evaluation
Chapter_06	Chapter_06/Exercise_6-03_Model_Card_and_NIST_AI_RMF_Mapping.ipynb	Worksheet	NVIDIA Model Card++ (Bias, Explainability, Privacy, Safety & Security subcards), NIST AI RMF 1.0 (Govern, Map, Measure, Manage), EU AI Act risk tiers, SHAP vs. LIME

Chapter_07	Chapter_07/Lab_7-01_Zero_Shot_Few_Shot_Chain_of_Thought_and_Sampling.ipynb	Hosted-API lab	24-item benchmark across Zero-Shot, Few-Shot, Zero-Shot CoT, Few-Shot CoT, and Self-Consistency (majority vote); Majority/Recency bias; decoding math for temperature, top_k, and top_p
Chapter_07	Chapter_07/Lab_7-02_Prompt_Injection_Attack_and_Defense.ipynb	Hosted-API lab	Direct vs. Indirect Prompt Injection (poisoned RAG docs) & System Prompt Leakage; layered defenses (XML delimiters + tag escaping, Sandwich Defense, Canary Tokens + JSON schema validation, Guardrails)

Chapter_08	Chapter_08/Lab_8-01_Tokenizers_and_the_Three_Architecture_Families.ipynb	Notebook lab	BPE (gpt2) vs. WordPiece (bert) vs. SentencePiece/Unigram (t5) subword splits & fertility; Scaled Dot-Product Attention ($\frac{QK^T}{\sqrt{d_k}}$); Encoder-Only (BERT) vs. Decoder-Only (GPT) vs. Encoder-Decoder (T5)
Chapter_08	Chapter_08/Lab_8-02_Quantization_and_Inference_Cost.ipynb	Notebook lab (GPU)	Model compression (PTQ vs. QAT, Distillation, 2:4 Structured Pruning), BitsAndBytesConfig, live FP32 / FP16 / INT8 / INT4 (NF4) quantization benchmark, memory sizing & cloud GPU cost calculator
Chapter_08	Chapter_08/Exercise_8-03_Choose_the_Optimization_Strategy.ipynb	Worksheet	TensorRT-LLM (In-Flight Batching, Paged KV Cache, Speculative Decoding, FlashAttention/Kernel Fusion, Tensor vs. Pipeline Parallelism), Triton Inference Server (Model Ensembles), and NVIDIA NIM


