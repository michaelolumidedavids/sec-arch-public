# Optional AI assistance

SecArch works fully without AI. The review and the threat model run on built in rules and a built in threat library. If you want a second opinion, you can switch on AI assistance and use your own key or a model on your own computer. It is **off by default**.

## What it does

When AI assistance is on, **Run review** and **Regenerate** (threat model) also pass a description of your design to the AI model you chose. The model checks each finding and each threat, and adds issues the rules did not find. Where the AI and a rule disagree, the AI result is used. The reports and tables show the final result only.

If the AI call fails (no internet, bad key, rate limit), SecArch shows a short note and uses the rules only. Findings you have already triaged or edited are never dismissed by the AI.

## Choose a provider

| Provider | Cost | Key starts with | Notes |
|---|---|---|---|
| **Groq** | Free tier, no card | `gsk_` | Free plan is limited to about 8,000 tokens a minute, so a large design takes several minutes. |
| **Google Gemini** | Free tier, no card | `AIza` | Fast. On the free plan Google may use prompts to improve its products outside the UK, EU and EEA. |
| **OpenRouter** | Very low cost per use. Some models are free (names ending `:free`, about 50 requests a day until you add credit) | `sk-or-` | Free models come and go. Use **Test connection** to see what is available. Data handling depends on the company serving the model. |
| **Claude (Anthropic)** | Billed per use on your Anthropic API account | `sk-ant-` | A Claude chat subscription is separate from the API. Create a key in the Anthropic Console. |
| **OpenAI** | Billed per use on your OpenAI API account | `sk-` | A ChatGPT subscription is separate from the API. Create a key on the OpenAI platform and add credit there. |
| **Ollama (local)** | Free | none | Runs on your own computer, so the design never leaves it. Needs Ollama installed and a model downloaded. |

Provider terms, limits and prices change. Check the provider's own pages before you rely on a free tier.

## Set it up (hosted providers)

1. Open **Review Security Design** or **Create Threat Model** and click **AI settings**. You can also use the menu **View, AI settings...**.
2. Tick **Use AI assistance**.
3. Choose a **Provider**.
4. Click **Get a key** under the key box. This opens the provider's page. Create a key there and copy it.
5. Paste it into **API key**.
6. Leave the **Model** as suggested, or choose another. Click **Test connection**. A message such as **Connected. 12 models available.** confirms the key works.
7. Leave **Hide names before sending** ticked (recommended). Components, connections, zones and data are sent as labels such as C1 and F2, and your real names are put back in the results.
8. Read **What is sent** and **What is not sent**, then tick **I understand design details will be sent to this provider when I run a review or threat model, and I am allowed to share them**. You give this agreement for each provider.
9. Click **Done**. The panel says **AI assistance is on.** when everything is ready. If it says **Add a key and pick a model to finish.** or **Tick the agreement above to finish.**, complete that step.

Run the review or threat model as usual. A progress message shows while the AI works.

## Set it up (Ollama, on your own computer)

1. Install Ollama from [ollama.com/download](https://ollama.com/download) and start it.
2. Download a model, for example by running `ollama pull` followed by a model name in a terminal.
3. In SecArch, open **AI settings**, tick **Use AI assistance**, choose **Ollama (local)**, and leave the address as `http://localhost:11434` unless you changed it.
4. Click **Test connection**, choose a model from the list, then **Done**.

The desktop app talks to Ollama on your own computer directly. Nothing leaves your machine.

## What is sent and what is not

**Sent:** component types, technologies, security settings, connections, trust zones, data classifications, and the text of the findings and threats. With **Hide names** on, your names are replaced by labels.

**Not sent:** your `.secarc` file, diagram images, report files, your email address or any account detail.

## Your key

* The key is kept in the app on your computer and is sent only to the provider you chose.
* By default it is forgotten when you close the app. Tick **Remember the key on this device** to keep it between sessions.
* A remembered key is stored in the app's local data folder as plain data. It is not encrypted by SecArch. Do not tick it on a shared computer.
* To remove it, clear the **API key** box, or untick **Remember the key on this device**.

## Turn it off

Open **AI settings**, untick **Use AI assistance** and click **Done**. Reviews and threat models then use the built in rules only.
