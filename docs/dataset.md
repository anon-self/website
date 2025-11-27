---
layout: default
title: Dataset
nav_order: 2
description: "Mobile Application Coverage: The 25% Curse and Ways Forward"
permalink: /docs/dataset
---

<script type="text/javascript">
        function showHideRow(row) {
            //$("#" + row).toggle();
        }
</script>

<style>
    table {
        overflow-x: auto;
        display: block;
        table-layout:fixed;
        white-space: nowrap;
    }
    .table_dataset .hidden_info {
        display: none;
    }
    .table_dataset {
        border-collapse: collapse;
    }
    .table_dataset tr.app_short:hover td {
        /*background-color: #E6E6FA;*/
    }
    
    td.app, th.app {
        min-width: 150px
    }

    td.package, th.package {
        min-width: 285px
    }
    
</style>


<!--
### Selected Google Play Applications

Here put a list of all the applications and on click show the detailed info from the table, should be loaded from excel !-->

We experiment on three application benchmarks:

<!--
### Selected Benchmark Applications


We also experiment on a subset applications from the [AndroTest dataset](http://www.cc.gatech.edu/∼orso/software/androtest). From 68 applications originally present in the dataset, we exclude 7 apps which crash on startup and for which we can not reliably identify source code.

We reconstitute the dataset by selecting the latest available version for each of the 61 applications as of 2023.
We further divide it into two datasets depending on whether the applications are also available on the Google Play Store or not, namely:
-->

#### BenchNotGP: 47 open-source apps from [AndroTest](http://www.cc.gatech.edu/∼orso/software/androtest), not on the Google Play Store

<table id="table_bgp" class="table_dataset">
    <thead>
        <tr>
            <th style="text-align: left" class="app"> Application</th>
            <th style="text-align: left"  class="package"> Package Name</th>
            <th style="text-align: left"> Used Version (Latest)</th>
            <th style="text-align: left"> Original Version</th>
            <th style="text-align: left"> Year</th>
            <th style="text-align: left"> Source</th>
            <th style="text-align: left"> # Activities</th>
            <th style="text-align: left"> Minimum SDK</th>
            <th style="text-align: left"> Target SDK</th>
            <th style="text-align: left"> # Permissions (in Manifest)</th>
            <th style="text-align: left"> # Features (in Manifest)</th>
        </tr>
    </thead>
    <tbody>
    {% for value in site.data.benchnotgp-info %}
    {% assign tr_id = 'hidden_info_bngp' | append: forloop.index %}
    {% assign onClickFunc = "showHideRow('" | append: tr_id | append: "')" %}
    <tr onClick="{{ onClickFunc }}" class="app_short">
        <td style="text-align: left" class="app"> {{ value.application_name }}</td>
        <td style="text-align: left" class="package"> {{ value.package_name }}</td>
        <td style="text-align: left"> {{ value.current_version }}</td>
        <td style="text-align: left"> {{ value.original_version }}</td>
        <td style="text-align: left"> {{ value.year }}</td>
        <td style="text-align: left"> {{ value.source }}</td>
        <td style="text-align: left"> {{ value.activities }}</td>
        <td style="text-align: left"> {{ value.min_sdk }}</td>
        <td style="text-align: left"> {{ value.target_sdk }}</td>
        <td style="text-align: left"> {{ value.num_permissions }}</td>
        <td style="text-align: left"> {{ value.num_features }}</td>
    </tr>
    <tr id= {{ tr_id }} class="hidden_info">
    <!--td></td-->
    <td colspan="10">
        <table>
            <thead>
                <tr>
                    <th style="text-align: left"> List of permissions (in Manifest)</th>
                </tr>
            </thead>
            <tbody>
                {% assign permissions = value.permissions | split: "; " %}
                <tr>
                    <td style="text-align: left"> 
                    {% for permission in permissions %}
                        <tr> <td>{{ permission }}</td></tr>
                    {% endfor %}
                    </td>
                </tr>
                {% assign features = value.features | split: "; " %}
                <thead>
                    <tr>
                        <th style="text-align: left"> List of features (in Manifest)</th>
                    </tr>
                </thead>
                <tr>
                    <td style="text-align: left"> 
                    {% for feature in features %}
                        <tr> <td>{{ feature | split: "implied" | first}}</td></tr>
                    {% endfor %}
                    </td>
                </tr>
            </tbody>
        </table>
    </td>
    </tr>
    {% endfor %}
    </tbody>
</table>

<!--a href="../assets/images/benchgp.png">
    <img
        src="../assets/images/benchgp.png"
        alt="Selected Benchmark Applications (on Google Play)"
    >
</a>

<a href="../assets/images/benchnotgp.png">
    <img
        src="../assets/images/benchnotgp.png"
        alt="Selected Benchmark Applications (not on Google Play)"
    >
</a-->

---

#### BenchGP: 14 open-source apps from [AndroTest](http://www.cc.gatech.edu/∼orso/software/androtest), also available on Google Play Store

<table id="table_bgp" class="table_dataset">
    <thead>
        <tr>
            <th style="text-align: left" class="app"> Application</th>
            <th style="text-align: left" class="package"> Package Name</th>
            <th style="text-align: left"> Used Version (Latest)</th>
            <th style="text-align: left;">Original Version</th>
            <th style="text-align: left"> Year</th>
            <th style="text-align: left"> Source</th>
            <th style="text-align: left"> # Activities</th>
            <th style="text-align: left"> Minimum SDK</th>
            <th style="text-align: left"> Target SDK</th>
            <th style="text-align: left"> # Permissions (in Manifest)</th>
            <th style="text-align: left"> # Features (in Manifest)</th>
        </tr>
    </thead>
    <tbody>
    {% for value in site.data.benchgp-info %}
    {% assign tr_id = 'hidden_info_bgp' | append: forloop.index %}
    {% assign onClickFunc = "showHideRow('" | append: tr_id | append: "')" %}
    <tr onClick="{{ onClickFunc }}" class="app_short">
        <td style="text-align: left" class="app"> {{ value.application_name }}</td>
        <td style="text-align: left" class="package"> {{ value.package_name }}</td>
        <td style="text-align: left"> {{ value.current_version }}</td>
        <td style="text-align: left"> {{ value.original_version }}</td>
        <td style="text-align: left"> {{ value.year }}</td>
        <td style="text-align: left"> {{ value.source }}</td>
        <td style="text-align: left"> {{ value.activities }}</td>
        <td style="text-align: left"> {{ value.min_sdk }}</td>
        <td style="text-align: left"> {{ value.target_sdk }}</td>
        <td style="text-align: left"> {{ value.num_permissions }}</td>
        <td style="text-align: left"> {{ value.num_features }}</td>
    </tr>
    <tr id= {{ tr_id }} class="hidden_info">
    <!--td></td-->
    <td colspan="11">
        <table>
            <thead>
                <tr>
                    <th style="text-align: left"> List of permissions (in Manifest)</th>
                </tr>
            </thead>
            <tbody>
                {% assign permissions = value.permissions | split: "; " %}
                <tr>
                    <td style="text-align: left"> 
                    {% for permission in permissions %}
                        <tr> <td>{{ permission }}</td></tr>
                    {% endfor %}
                    </td>
                </tr>
                {% assign features = value.features | split: "; " %}
                <thead>
                    <tr>
                        <th style="text-align: left"> List of features (in Manifest)</th>
                    </tr>
                </thead>
                <tr>
                    <td style="text-align: left"> 
                    {% for feature in features %}
                        <tr> <td>{{ feature | split: "implied" | first}}</td></tr>
                    {% endfor %}
                    </td>
                </tr>
            </tbody>
        </table>
    </td>
    </tr>
    {% endfor %}
    </tbody>
</table>

---

#### TopGP: 42 top-ranked free apps from the Google Play Store, [available for download here](https://zenodo.org/records/14958990/files/MobileCoverage.zip?download=1)

<table id="table_topgp" class="table_dataset">
    <thead>
        <tr>
            <th style="text-align: left"> Application</th>
            <th style="text-align: left"> Package Name</th>
            <th style="text-align: left"> Version</th>
            <th style="text-align: left"> Category</th>
            <th style="text-align: left"> Downloads</th>
            <th style="text-align: left"> Popularity</th>
            <th style="text-align: left"> # Activities</th>
            <th style="text-align: left"> Minimum SDK</th>
            <th style="text-align: left"> Target SDK</th>
            <th style="text-align: left"> # Permissions (in Manifest)</th>
            <th style="text-align: left"> # Features (in Manifest)</th>
        </tr>
    </thead>
    <tbody>
    {% for value in site.data.topgp-info %}
    {% assign tr_id = 'hidden_info_gp' | append: forloop.index %}
    {% assign onClickFunc = "showHideRow('" | append: tr_id | append: "')" %}
    <tr onClick="{{ onClickFunc }}" class="app_short">
        <td style="text-align: left"> {{ value.application_name }}</td>
        <td style="text-align: left"> {{ value.package_name }}</td>
        <td style="text-align: left"> {{ value.version }}</td>
        <td style="text-align: left"> {{ value.category }}</td>
        <td style="text-align: left"> {{ value.downloads }}</td>
        <td style="text-align: left"> {{ value.popularity_rank }}</td>
        <td style="text-align: left"> {{ value.activities }}</td>
        <td style="text-align: left"> {{ value.min_sdk }}</td>
        <td style="text-align: left"> {{ value.target_sdk }}</td>
        <td style="text-align: left"> {{ value.num_permissions }}</td>
        <td style="text-align: left"> {{ value.num_features }}</td>
    </tr>
    <tr id= {{ tr_id }} class="hidden_info">
    <!--td></td-->
    <td colspan="11">
        <table>
            <thead>
                <tr>
                    <th style="text-align: left"> List of permissions (in Manifest)</th>
                </tr>
            </thead>
            <tbody>
                {% assign permissions = value.permissions | split: "; " %}
                <tr>
                    <td style="text-align: left"> 
                    {% for permission in permissions %}
                        <tr> <td>{{ permission }}</td></tr>
                    {% endfor %}
                    </td>
                </tr>
                {% assign features = value.features | split: "; " %}
                <thead>
                    <tr>
                        <th style="text-align: left"> List of features (in Manifest)</th>
                    </tr>
                </thead>
                <tr>
                    <td style="text-align: left"> 
                    {% for feature in features %}
                        <tr> <td>{{ feature | split: "implied" | first}}</td></tr>
                    {% endfor %}
                    </td>
                </tr>
            </tbody>
        </table>
    </td>
    </tr>
    {% endfor %}
    </tbody>
</table>

<!--a href="../assets/images/apps-latest.png">
    <img
        src="../assets/images/apps-latest.png"
        alt="Selected Google Play Applications"
    >
</a-->

<div style="text-align: left"> 
    All information provided above about the dataset, as well as the full list of permissions and features used by each app, can be downloaded as an <a href="assets/data/Dataset.xlsx">excel file</a>.
</div>

---

<!--We provide additional details about the selected applications namely the application size, targeted SDK version and used permissions in this [excel file](assets/data/BenchInfo.xlsx).-->
