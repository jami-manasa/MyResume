# gcp_cm


<details><summary><b>Common Imports for all Python Scripts:</b></summary>
<br>Import discovery module from Python client library for Google API<br>
    - <b>from googleapiclient import discovery</b>

<br>Import service_account module from Google auth library for Google API to authenticate goolge cloud console using service_account_file<br>
    - **from google.oauth2 import service_account**
</details>



<details><summary><b>01. virtual_machines.py</b></summary>
<br>

**Description:**
This script is to fetch the details of Google Cloud Platform(GCP) virtual_machine_instance details from Google Cloud Console and does insert / update/ delete operations on gs.virtual_machines_instances table.

**Script Execution / Functional Flow**

- [ ] Fetch the list of Google Cloud Platform(GCP) projects from gs.gcp_projects table
- [ ] Loop through the list of GCP Projects
- [ ] Get the zone wise virtual_machine_instance details of a GCP Project by creating compute_client using discovery module of Google API client for Python
- [ ] Process the virtual_machine_instances response into a dataframe
- [ ] If the dataframe is empty Remove records of specific Project from gs.virtual_machine_instances table by Project_Id
- [ ] If the dataframe is not empty Update / Insert records of specific Project into gs.virtual_machine_instances table by Project_Id


![alt text](https://public.boxcloud.com/api/2.0/internal_files/878334383930/versions/944093305130/representations/png_paged_2048x2048/content/1.png?access_token=1!CJ44wL08T85sdw8HlQV8eKEJQx_-yHqF2gZMmK0ziXXBKdHa5oJ-x4u-Rp2C1y6xIjeY92mMUKM-4FNrV-I_Xr-x5n6lhzY2c-7-Wedc0mrVvLIanaEDiR_CjRhABOi81TLoa2w6vm2gT0kWWBCx973OfY6gc4VauAe-_fd-DEMvznbA93w-Zq08NLYj72-GgjVK1Ba9qpMUS4CeWKZRr8l5kc8AlOLxqPylcvlfr16h_wRH3HCwrAOxDIYLSR5pMF4QVkytPFGy62ThKtN6XS-kAb_w6LlRyQ1Gk1CW8goCy5xEjwnKHdOu1uaGlaW42Z-ktfujJ3O4aFfKuPuYbgRhZFiSrdZC05WpnwvT1_Mo4G0CSdtIZIqtLdvD2micOslu_7_ZJX4X2ZudhjIz475LDi5leyrj2k9hhsfk2uR-oKs5Kjar05abunSxKjnVUiFDziC_J3FZ1vrq-VMSbs_VKvnOLMOx7ZsNiu8E8nnp9cnFvhYoQob4G9bp67wWnXspiwc6zkxHiYu2dbJuXwjYlaHTqHaaJcRVUr0LjJJL2Pa9P3bMVGZbMNZ0W0FznsW3OKLvNNE-_2-9chvOlwU7fQ0jiAy72cwqOr_vdpfb9VRo9KqxpYpKcanwFr0NWb-jQVZ2jUffLgqddZYta_0T25N0mVy17cg9dolyaP9izQbj&amp;box_client_name=box-content-preview&amp;box_client_version=2.80.0)
</details>


<details><summary><b>02. sql_databases.py</b></summary>
<br>

**Description:**
This script is to fetch the details of Google Cloud Platform(GCP) sql_database_instance details from Google Cloud Console and does insert / update/ delete operations on gs.sql_databases table.

**Script Execution / Functional Flow**

- [ ] Fetch the list of Google Cloud Platform(GCP) projects from ad.gcp_projects table
- [ ] Loop through the list of GCP Projects
- [ ] Get the sql_database_instance details of a GCP Project by creating sqladmin_client using discovery module of Google API client for Python
- [ ] Process the sql_database_instances response into a dataframe
- [ ] If the dataframe is empty Remove records of specific Project from gs.sql_databases table by Project_Id
- [ ] If the dataframe is not empty Update / Insert records of specific Project into gs.sql_databases table by Project_Id


![alt text](https://public.boxcloud.com/api/2.0/internal_files/878346942199/versions/944108053399/representations/png_paged_2048x2048/content/1.png?access_token=1!TcBj0hzw7dnAjT9k4CU4liSMGCVWG6WyqC-EvzXYrVmgwkE9lYdtoMPufVs19_VZIuUMnEcXO_78y7lQxDEy9f153-2oCvR_iDxY9kMYIesJcqTmEtRU9S7Oygqq_ilug1ErHEqZtBXwhKnh2Mgp8yO8wQUo951S47vC-cRBIofxcOaG8KZ56RhXE_XEaaF9IHTRK4Z3kkyWhV5WUFID6tAFfwy4zM-s-FWV0Dvnp8MSNEnwR_WBCGYbKZrWY6iotMn8iYQzVChRmEU8EorBmq5u41einsmdduD90soHhEUz0jEMJ4_V4yxQupBguUGCz25hracX0DNeZP06_FCie6cla-Y0ksD1eqCW97SE2FEepsCOiBgp-KiMzKgdQCqtbSMpWxGkbR9E8-sZYftP389AlREsB-1dGO4ils62Ofk1OP7rvH_ReSvG92t1b-yELGyL12JQuHUQgrTPKazlkOoaE7K3m6NK5lmJWR8CmTBPM2Peww4jZGYswbkJIt1hMJq8AktOWqB3_lMqFn0ljuJ0194MMCDouMrqKn_LzyoklVc9u7fbwfQppovc9BktDR4EhYQ_liYKogEh_dr-487rlh_DbaTb9RiOXbhZ2ExYgDhFMKecE-TtWrV8NTX-TnvMn3SKZkCjaj_GTx0HhqenvHEBG2ETjaUDkY1nPjUxJ-Zd&amp;box_client_name=box-content-preview&amp;box_client_version=2.80.0)
</details>

    
