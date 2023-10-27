# Data Dictionary

## Table of Contents

- [Data Dictionary](#data-dictionary)
  - [Summary](#summary)
  - [Entities](#entities)
    - [User](#user)
    - [Term](#term)
    - [History](#history)
    - [Cycle](#cycle)
    - [Cultivation](#cultivation)
    - [Grain Seed](#grain-seed)
    - [Irrigation](#irrigation)
    - [Soil](#soil)
    - [Enterprise](#enterprise)
    - [Operation](#operation)
    - [State](#state)
    - [City](#city)
    - [Land](#land)
    - [Property](#property)
  - [Types](#types)
    - [Finality](#finality)
    - [Activity](#activity)
    - [Modality](#modality)
    - [Product](#product)
    - [Variety](#variety)
    - [Hamper](#hamper)
    - [Zoning](#zoning)

<div style="page-break-after: always;"></div>

## Entities

### User

Table: **usr_usuario** \
Description: System users.

| Attribute         | Type      | Size      | Constraint        | Default Value | Description
|:------------------|:----------|:---------:|:-----------------:|:-------------:|:-
| usr_id            | Integer   | -         | Primary key       | -             | User identifier.
| usr_nome          | Text      | 150       | -                 | -             | User name.
| usr_doc           | Text      | 14        | -                 | -             | User document number.
| usr_proprietario  | Boolean  | -         | -                 | -             | Check if user is owner.
| usr_email         | Text      | 255       | -                 | -             | User e-mail.
| usr_senha         | Text      | 255       | -                 | -             | User password hash.
| usr_permissao     | Boolean  | -         | -                 | -             | User data use authorization.
| usr_adm           | Boolean  | -         | -                 | -             | Check if the user is system administrator.

<div style="page-break-after: always;"></div>

### Term

Table: **trm_termo** \
Description: Terms of acceptance for using the system.

| Attribute         | Type          | Size      | Constraint        | Default Value | Description
|:------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| trm_id            | Integer       | -         | Primary key       | -             | Term identifier.
| trm_Date          | Date          | -         | -                 | -             | Term creation date.
| trm_proprietario  | Boolean      | -         | -                 | -             | Term data use authorization.
| trm_text          | Text          | -         | -                 | -             | Term content.

### History

Table: **htr_historico** \
Description: History of acceptance of terms by users.

| Attribute         | Type      | Size  | Constraint  | Default Value | Description
|:------------------|:----------|:-----:|:-----------:|:-------------:|:-
| [htr_usr](#user)  | Integer   | -     | Foreign Key | -             | User identifier.
| [hrt_trm](#term)  | Integer   | -     | Foreign Key | -             | Term identifier.
| hrt_Date          | Date      | -     | -           | -             | Date of acceptance of terms.

- **htr_usr** references [**usr_usuario(usr_id)**](#user)
- **hrt_trm** references [**trm_termo(trm_id)**](#term)

<div style="page-break-after: always;"></div>

### Cycle

Table: **ccl_ciclo** \
Description: Types of cycles.

| Attribute         | Type          | Size      | Constraint        | Default Value | Description
|:------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| ccl_id            | Integer       | -         | Primary key       | -             | Cycle identifier.
| ccl_descricao     | Text          | -         | -                 | -             | Type of cycle in full.

### Cultivation

Table: **clt_cultivo** \
Description: Types of cultivation.

| Attribute         | Type          | Size      | Constraint        | Default Value | Description
|:------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| clt_id            | Integer       | -         | Primary key       | -             | Cultivation identifier.
| clt_descricao     | Text          | 150       | -                 | -             | Type of cultivation in full.

<div style="page-break-after: always;"></div>

### Grain Seed

Table: **gsm_grao_semente** \
Description: Indicates of whether it is a grain or seed.

| Attribute         | Type          | Size      | Constraint        | Default Value | Description
|:------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| gsm_id            | Integer       | -         | Primary key       | -             | Grain or Seed identifier.
| gsm_descricao     | Text          | 150       | -                 | -             | Description of whether it is a grain or seed.

### Irrigation

Table: **irg_irrigacao** \
Description: Types of irrigation.

| Attribute         | Type          | Size      | Constraint        | Default Value | Description
|:------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| irg_id            | Integer       | -         | Primary key       | -             | Irrigation identifier.
| irg_descricao     | Text          | 150       | -                 | -             | Type of irrigation in full.

<div style="page-break-after: always;"></div>

### Soil

Table: **sol_solo** \
Description: Types of foil.

| Attribute         | Type          | Size      | Constraint        | Default Value | Description
|:------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| sol_id            | Integer       | -         | Primary key       | -             | Soil identifier.
| sol_descricao     | Text          | 150       | -                 | -             | Type of soil in full.

### Enterprise

Table: **emp_empreendimento** \
Description: Enterprise where the operations occurs.

| Attribute         | Type          | Size      | Constraint        | Default Value | Description
|:------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| emp_id            | Integer       | -         | Primary key       | -             | Enterprise identifier.
| emp_finalidade    | Finality      | -         | -                 | -             | Enterprise finality.
| emp_atividade     | Activity      | -         | -                 | -             | Type of activity.
| emp_modalidade    | Modality      | -         | -                 | -             | Enterprise modality.
| emp_prodduto      | Product       | -         | -                 | -             | Product produced.
| emp_variedade     | Variety       | -         | -                 | -             | Enterprise variety.
| emp_cesta         | Hamper        | -         | -                 | -             | Enterprise type of harvest.
| emp_zoneamento    | Zoning        | -         | -                 | -             | Zoning status.

<div style="page-break-after: always;"></div>

### Operation

Table:**opr_operacao** \
Description: Planting and harvesting operations.

| Attribute                     | Type      | Size      | Constraint  | Default Value | Description
|:------------------------------|:----------|:---------:|:-----------:|:-------------:|:-
| opr_id                        | Integer   | -         | Primary key | -             | Operation identifier.
| opr_inicio_plantio            | Date      | -         | -           | -             | Planting initial date.
| opr_fim_plantio               | Date      | -         | -           | -             | Planting final date.
| opr_inicio_colheita           | Date      | -         | -           | -             | Harvesting initial date.
| opr_fim_colheita              | Date      | -         | -           | -             | Harvesting final date.
| [opr_std](#state)             | Integer   | -         | Foreign Key | -             | State identifier.
| [opr_mun](#city)              | Integer   | -         | Foreign Key | -             | City identifier.
| [opr_sol](#soil)              | Integer   | -         | Foreign Key | -             | Type of soil identifier.
| [opr_irg](#irrigation)        | Integer   | -         | Foreign Key | -             | Type of irrigation identifier.
| [opr_clt](#cultivation)       | Integer   | -         | Foreign Key | -             | Type of cultivation identifier.
| [opr_gsm](#grain-seed)        | Integer   | -         | Foreign Key | -             | Grain or seed identifier.
| [opr_ccl](#cycle)             | Integer   | -         | Foreign Key | -             | Type of cycle identifier.
| [opr_emp](#enterprise)        | Integer   | -         | Foreign Key | -             | Enterprise identifier.

- **opr_std** references [**std_estado(std_id)**](#state);
- **opr_mun** references [**mun_municipio(mun_id)**](#city);
- **opr_sol** references [**sol_solo(sol_id)**](#soil);
- **opr_irg** references [**irg_irrigacao(irg_id)**](#irrigation);
- **opr_clt** references [**clt_cultivo(clt_id)**](#cultivation);
- **opr_gsm** references [**gsm_grao_semente(gsm_id)**](#grain-seed);
- **opr_ccl** references [**ccl_ciclo(ccl_id)**](#cycle);
- **opr_emp** references [**emp_empreendimento(emp_id)**](#enterprise).

<div style="page-break-after: always;"></div>

### State

Table: **std_estado** \
Description: Federative state.

| Attribute     | Type          | Size      | Constraint        | Default Value | Description
|:--------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| std_id        | Integer       | -         | Primary key       | -             | State identifier.
| std_descricao | Text          | 2         | -                 | -             | State acronym.

### City

Table: **mun_municipio** \
Description: City where the operations occurs.

| Attribute     | Type          | Size      | Constraint        | Default Value | Description
|:--------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| mun_id        | Integer       | -         | Primary key       | -             | City identifier.
| mun_descricao | Text          | 255       | -                 | -             | Name of the city.

<div style="page-break-after: always;"></div>

### Land

Table: **glb_gleba** \
Description: Land where the operations occurs.

| Attribute             | Type      | Size      | Constraint        | Default Value | Description
|:----------------------|:----------|:---------:|:-----------------:|:-------------:|:-
| glb_id                | Integer   | -         | Primary key       | -             | Land identifier.
| glb_poligono          | Polygon   | 4326      | -                 | -             | Land perimeter points.
| [glb_opr](#operation) | Integer   | -         | Foreign Key       | -             | Operation identifier.

- **glb_opr** references [**opr_operacao(opr_id)**](#operation)

### Property

Table: **prp_propriedade** \
Description: Property where the operations occurs.

| Attribute             | Type          | Size      | Constraint        | Default Value | Description
|:----------------------|:--------------|:---------:|:-----------------:|:-------------:|:-
| prp_id                | Integer       | -         | Primary key       | -             | Property identifier.
| prp_doc               | Text          | 14        | -                 | -             | Property document registration.
| prp_sncr              | Text          | 255       | -                 | -             | Sistema Nacional de Cadastro Rural registration.
| prp_nirf              | Text          | 255       | -                 | -             | Cadastro Nacional de Imóvel Rural registration.
| prp_car               | Text          | 255       | -                 | -             | Cadastro Ambiental Rural registration.
| [prp_opr](#operation) | Integer       | -         | Foreign Key       | -             | Operation identifier.

- **prp_opr** references [**opr_operacao(opr_id)**](#operação)

<div style="page-break-after: always;"></div>

## Types

### Finality

Name: finalidade_type \
Description: Enterprise finality. \
Options:

- Custeio
- Comercialização

### Activity

Name: atividade_type \
Description: Enterprise types of activity. \
Options:

- Agrícola

<div style="page-break-after: always;"></div>

### Modality

Name: modalidade_type \
Description: Enterprise types of modality. \
Options:

- LAVOURA
- BENEFICIAMENTO OU INDUSTRIALIZAÇÃO
- FEPM (EX-EGF) - encerrado
- FEE (EX-LEC)
- PRÉ-COMERCIALIZAÇÃO - encerrado
- DESCONTO (NPR E DR)
- CPR (CÉDULA DE PRODUTO RURAL)
- ESTOCAGEM
- FGPP-Financiamento para Garantia de Preços ao Prod
- COVID-19 - Resolução 4801/2020
- ESTIAGEM - Resolução 4802/2020
- Financiamento para Aquisição da Produção/Materia P
- Aquisição de Matéria Prima direto do Produtor/Coop

### Product

Name: produto_type \
Description: Types of product. \
Options:

- SOJA

<div style="page-break-after: always;"></div>

### Variety

Name: variedade_type \
Description: Enterprise variety. \
Options:

- NÃO SE APLICA
- CULTIVO EM SISTEMAS INTEGRADOS
- VARIEDADE
- SEMENTE
- FARELO
- ÓLEO BRUTO DEGOMADO
- EM GRÃOS
- ÓLEO

### Hamper

Name: cesta_type \
Description: Types of harvest. \
Options:

- Irrigadas
- Safra de Verão (1ª Safra)
- Safrinha (2ª Safra)
- Ano Civil / Ano de Exploração

### Zoning

Name: zoneamento_type \
Description: Zoning status. \
Options:

- Não zoneado
- Zoneado
