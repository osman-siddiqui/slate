---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Sema4 CAV API!  API is for internal Sema4 use only to access Knowledge base API endpoints, which can get information on various variants, and  clinical trials in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

CAV-API uses API keys to allow access to the API. You can register a new CAV-API API key at our [developer portal](http://example.com/developers).

CAV-API expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Sema4 Report Narrative

## Get up to date Report Narrative

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "curl -d "op=load&mutation_type=SNV&entity=chr7:g.55241708G>C&disease=LUAD" -X POST 34.235.93.148/CAV-API/postNarrativeService.php"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
      "gene": "EGFR",
      "gDNA": "chr7:g.55241708G>C",
      "var": "p.G719A",
      "cancer": "Lung",
      "oncotree": "LUAD",
      "narrative": "<p><strong>EGFR-<em>p.G719A\/C\/S<\/em>- NSCLC<\/strong><\/p><p><strong><em>Gene Function and Clinical Relevance<\/em>: <\/strong>The<strong> <\/strong><em>EGFR <\/em>gene encodes for Epidermal Growth Factor Receptor (EGFR) protein, which is a member of the family receptor tyrosine kinases (RTKs). Binding of EGFR to its ligand, EGF results in phosphorylation and subsequent activation of the downstream PI3K-AKT-mTOR and RAS-RAF-MEK-ERK pathways. Somatic activating mutations and increased copy number of the <em>EGFR<\/em> gene occur in multiple cancers including glioma (44-71%), lung (19-32%), head and neck squamous cell carcinomas (10-15%) and stomach cancers (7-17%) (TCGA, provisional, PMID: 28481359).<\/p><p><strong><em>Alteration and Frequency<\/em>: <\/strong><em>EGFR<\/em> p.Gly719Ala\/Cys\/Ser (p.G719A\/C\/S) mutations in exon 18 are activating mutations in the kinase domain and yielding a change of glycine to an alanine\/cysteine\/serine. EGFR G719 mutations occur in 4-5% of all EGFR-mutated non-small cell line cancers. The G719A, G719C, and G719S occur in 2.1-2.2%, 0.9% and 0.9% of all EGFR mutated NSCLC separately (TCGA, provisional, PMID: 28481359). <\/p><p><strong><em>Prognostic Implications<\/em><\/strong>: In an analysis of 1201 patients with lung adenocarcinoma, EGFR exon 18 (including G719) mutations are associated with shorter overall survival than EGFR ex19del or L858R mutation (PMID: 26354324).<\/p><p><strong><em>Therapeutic Implications<\/em>: <\/strong>FDA approved Afatinib for EGFR G719 mutations in NSCLC. The NCCN panel suggests to use Erlotinib, Gefitinib, Afatinib and Osimertinib<strong> <\/strong>to treat NSCLC patients with EGFR G719A\/C\/S mutations (NCCN Guidelines Version 6. 2017 Non-Small Cell Lung Cancer). Based on extensive clinical evidence,<strong> <\/strong><em>EGFR<\/em> G719A\/C\/S predict sensitivity to therapies targeting EGFR, including EGFR tyrosine kinase inhibitors, such as Erlotinib (PMID: 15638953, PMID: 21531810, PMID: 24285021), Gefitinib (PMID: 15118073, PMID: 14570950, PMID: 21531810, PMID: 16011858, PMID: 24285021), Afatinib (PMID: 26051236), Neratinib (PMID: 24285021), Osimertinib (PMID: 29151359, PMID: 28841389, Abstract #4130, EMSO 2017).<\/p>"
  }
]
```

This endpoint retrieves the most up to date report narrative.

### HTTP Request

`GET http://34.235.93.148/CAV-API/getNarrativeService.php?op=load&mutation_type=SNV&entity=chr12:g.25398285C%3EG&disease=HCC`


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
op | load | If set to true, the result will also include cats.
mutation_type | SNV | Four mutations types choices 'SNV', 'Fusion', 'splice' and 'CNV'.
entity | chr7:g.55241708G>C | Genomic coordinates.
Disease | LUAD | Tumor type specified using msk oncotree code. http://oncotree.mskcc.org/#/home
Somatic | YES | Somatic status

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get Clinical Trials

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl -d "op=ct&mutation_type=SNV&entity=chr7:g.55241708G>C&disease=LUAD"
    -X POST 34.235.93.148/CAV-API/postNarrativeService.php
    -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "Target": "EGFR",
  "Disease": "LUAD",
  "Drugs": "HS-10241",
  "NCT Number": "NCT02981108",
  "Title": "A Study to Evaluate Safety, PK and Efficacy of HS-10296 in Patients With NSCLC",
  "Phase": "Phase 1",
  "Inclusion Variants": "EGFR activating mutation (G719X, exon 19 deletion, L858R, L861Q), EGFR T790M mutation",
  "Location": "Pacific Cancer Medical Center, Inc., Anaheim, California, United States|Beverly Hills Cancer Center, Beverly Hills, California, United States|University of Colorado-1775 Aurora Court, Aurora, Colorado, United States",

}
```

This endpoint retrieves clinical trials based on Gene and Tumor(Oncotree_Code).

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
op | ct | If set to true, the result will also include cats.
mutation_type | SNV | Four mutations types choices 'SNV', 'Fusion', 'splice' and 'CNV'.
entity | chr7:g.55241708G>C | Genomic coordinates.
Disease | LUAD | Tumor type specified using msk oncotree code. http://oncotree.mskcc.org/#/home

## Upload an Updated Narrative

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl  -d "op=upload&narrative=this is a test narrative&entity=chr7:g.55241708G>C&disease=LUAD"
  -X POST 34.235.93.148/CAV-API/postNarrativeService.php
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "status": 200,
}
```

This uploads a new Report Style narrative.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
op | upload | If set to upload, the result will be inserted as New Narrative
narrative| Narrative text | Text of narrative
mutation_type | SNV | Four mutations types choices 'SNV', 'Fusion', 'splice' and 'CNV'.
entity | chr7:g.55241708G>C | Genomic coordinates.
Disease | LUAD | Tumor type specified using msk oncotree code. http://oncotree.mskcc.org/#/home
Somatic | YES | Somatic status
