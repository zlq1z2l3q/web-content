---
id: enable-dynamic-field.md
title: 启用动态字段
summary: ''
---
<h1 id="Enable-Dynamic-Field" class="common-anchor-header">启用动态字段<button data-href="#Enable-Dynamic-Field" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h1><p>本页介绍如何在集合中使用动态字段，以灵活插入和检索数据。</p>
<h2 id="Overview" class="common-anchor-header">概述<button data-href="#Overview" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>Milvus 允许你通过设置每个特定字段的名称和数据类型来定义集合的模式，以便在这些字段中创建索引，提高搜索性能。</p>
<p>一旦定义了字段，您就需要在插入数据时包含该字段。如果某些字段并不总是出现在所有数据条目中，该怎么办？这就是动态字段的用武之地。</p>
<p>集合中的动态字段是一个名为 $meta 的保留 JSON 字段。它可以将非模式定义的字段及其值作为键值对保存。使用动态字段，您可以搜索和查询模式定义的字段以及它们可能包含的任何非模式定义的字段。</p>
<h2 id="Enable-dynamic-field" class="common-anchor-header">启用动态字段<button data-href="#Enable-dynamic-field" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>在为集合定义模式时，可将<code translate="no">enable_dynamic_field</code> 设置为<code translate="no">True</code> 以启用预留动态字段，这表示以后插入的任何非模式定义字段及其值都将作为键值对保存在预留动态字段中。</p>
<p>下面的代码段创建了一个带有两个模式定义字段（即 id 和向量）的集合，并启用了动态字段。</p>
<div class="language-python">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/pymilvus/v2.4.x/MilvusClient/Collections/create_collection.md"><code translate="no">create_collection()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="language-java">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/java/v2.4.x/v2/Collections/createCollection.md"><code translate="no">createCollection()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="language-javascript">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/node/v2.4.x/Collections/createCollection.md"><code translate="no">createCollection()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="multipleCode">
   <a href="#python">Python </a> <a href="#java">Java</a> <a href="#javascript">Node.js</a></div>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">import</span> random, time
<span class="hljs-keyword">from</span> pymilvus <span class="hljs-keyword">import</span> connections, MilvusClient, DataType

SERVER_ADDR = <span class="hljs-string">&quot;http://localhost:19530&quot;</span>

<span class="hljs-comment"># 1. Set up a Milvus client</span>
client = MilvusClient(
    uri=SERVER_ADDR
)

<span class="hljs-comment"># 2. Create a collection</span>
schema = MilvusClient.create_schema(
    auto_id=<span class="hljs-literal">False</span>,
    enable_dynamic_field=<span class="hljs-literal">True</span>,
)

schema.add_field(field_name=<span class="hljs-string">&quot;id&quot;</span>, datatype=DataType.INT64, is_primary=<span class="hljs-literal">True</span>)
schema.add_field(field_name=<span class="hljs-string">&quot;vector&quot;</span>, datatype=DataType.FLOAT_VECTOR, dim=<span class="hljs-number">5</span>)

index_params = MilvusClient.prepare_index_params()

index_params.add_index(
    field_name=<span class="hljs-string">&quot;id&quot;</span>,
    index_type=<span class="hljs-string">&quot;STL_SORT&quot;</span>
)

index_params.add_index(
    field_name=<span class="hljs-string">&quot;vector&quot;</span>,
    index_type=<span class="hljs-string">&quot;IVF_FLAT&quot;</span>,
    metric_type=<span class="hljs-string">&quot;L2&quot;</span>,
    params={<span class="hljs-string">&quot;nlist&quot;</span>: <span class="hljs-number">1024</span>}
)

client.create_collection(
    collection_name=<span class="hljs-string">&quot;test_collection&quot;</span>,
    schema=schema,
    index_params=index_params
)

res = client.get_load_state(
    collection_name=<span class="hljs-string">&quot;test_collection&quot;</span>
)

<span class="hljs-built_in">print</span>(res)

<span class="hljs-comment"># Output</span>
<span class="hljs-comment">#</span>
<span class="hljs-comment"># {</span>
<span class="hljs-comment">#     &quot;state&quot;: &quot;&lt;LoadState: Loaded&gt;&quot;</span>
<span class="hljs-comment"># }</span>
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-java"><span class="hljs-keyword">import</span> io.milvus.v2.client.ConnectConfig;
<span class="hljs-keyword">import</span> io.milvus.v2.client.MilvusClientV2;
<span class="hljs-keyword">import</span> io.milvus.v2.common.DataType;
<span class="hljs-keyword">import</span> io.milvus.v2.common.IndexParam;
<span class="hljs-keyword">import</span> io.milvus.v2.service.collection.request.AddFieldReq;
<span class="hljs-keyword">import</span> io.milvus.v2.service.collection.request.CreateCollectionReq;
<span class="hljs-keyword">import</span> io.milvus.v2.service.collection.request.GetLoadStateReq;

<span class="hljs-type">String</span> <span class="hljs-variable">CLUSTER_ENDPOINT</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;http://localhost:19530&quot;</span>;

<span class="hljs-comment">// 1. Connect to Milvus server</span>
<span class="hljs-type">ConnectConfig</span> <span class="hljs-variable">connectConfig</span> <span class="hljs-operator">=</span> ConnectConfig.builder()
    .uri(CLUSTER_ENDPOINT)
    .build();

<span class="hljs-type">MilvusClientV2</span> <span class="hljs-variable">client</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class_">MilvusClientV2</span>(connectConfig);

<span class="hljs-comment">// 2. Create a collection in customized setup mode</span>

<span class="hljs-comment">// 2.1 Create schema</span>
CreateCollectionReq.<span class="hljs-type">CollectionSchema</span> <span class="hljs-variable">schema</span> <span class="hljs-operator">=</span> client.createSchema();

<span class="hljs-comment">// 2.2 Add fields to schema</span>
schema.addField(AddFieldReq.builder().fieldName(<span class="hljs-string">&quot;id&quot;</span>).dataType(DataType.Int64).isPrimaryKey(<span class="hljs-literal">true</span>).autoID(<span class="hljs-literal">false</span>).build());
schema.addField(AddFieldReq.builder().fieldName(<span class="hljs-string">&quot;vector&quot;</span>).dataType(DataType.FloatVector).dimension(<span class="hljs-number">5</span>).build());

<span class="hljs-comment">// 2.3 Prepare index parameters</span>
<span class="hljs-type">IndexParam</span> <span class="hljs-variable">indexParamForIdField</span> <span class="hljs-operator">=</span> IndexParam.builder()
    .fieldName(<span class="hljs-string">&quot;id&quot;</span>)
    .indexType(IndexParam.IndexType.STL_SORT)
    .build();

<span class="hljs-type">IndexParam</span> <span class="hljs-variable">indexParamForVectorField</span> <span class="hljs-operator">=</span> IndexParam.builder()
    .fieldName(<span class="hljs-string">&quot;vector&quot;</span>)
    .indexType(IndexParam.IndexType.IVF_FLAT)
    .metricType(IndexParam.MetricType.IP)
    .extraParams(Map.of(<span class="hljs-string">&quot;nlist&quot;</span>, <span class="hljs-number">1024</span>))
    .build();

List&lt;IndexParam&gt; indexParams = <span class="hljs-keyword">new</span> <span class="hljs-title class_">ArrayList</span>&lt;&gt;();
indexParams.add(indexParamForIdField);
indexParams.add(indexParamForVectorField);

<span class="hljs-comment">// 2.4 Create a collection with schema and index parameters</span>
<span class="hljs-type">CreateCollectionReq</span> <span class="hljs-variable">customizedSetupReq</span> <span class="hljs-operator">=</span> CreateCollectionReq.builder()
    .collectionName(<span class="hljs-string">&quot;customized_setup&quot;</span>)
    .collectionSchema(schema)
    .indexParams(indexParams)
    .enableDynamicField(<span class="hljs-literal">true</span>)
    .build();

client.createCollection(customizedSetupReq);

Thread.sleep(<span class="hljs-number">5000</span>);

<span class="hljs-comment">// 2.5 Get load state of the collection</span>
<span class="hljs-type">GetLoadStateReq</span> <span class="hljs-variable">customSetupLoadStateReq1</span> <span class="hljs-operator">=</span> GetLoadStateReq.builder()
    .collectionName(<span class="hljs-string">&quot;customized_setup&quot;</span>)
    .build();

<span class="hljs-type">boolean</span> <span class="hljs-variable">res</span> <span class="hljs-operator">=</span> client.getLoadState(customSetupLoadStateReq1);

System.out.println(res);

<span class="hljs-comment">// Output:</span>
<span class="hljs-comment">// true</span>
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-javascript"><span class="hljs-keyword">const</span> { <span class="hljs-title class_">MilvusClient</span>, <span class="hljs-title class_">DataType</span>, sleep } = <span class="hljs-built_in">require</span>(<span class="hljs-string">&quot;@zilliz/milvus2-sdk-node&quot;</span>)

<span class="hljs-keyword">const</span> address = <span class="hljs-string">&quot;http://localhost:19530&quot;</span>

<span class="hljs-keyword">async</span> <span class="hljs-keyword">function</span> <span class="hljs-title function_">main</span>(<span class="hljs-params"></span>) {
<span class="hljs-comment">// 1. Set up a Milvus Client</span>
client = <span class="hljs-keyword">new</span> <span class="hljs-title class_">MilvusClient</span>({address}); 

<span class="hljs-comment">// 2. Create a collection</span>
<span class="hljs-comment">// 2.1 Define fields</span>
<span class="hljs-keyword">const</span> fields = [
    {
        <span class="hljs-attr">name</span>: <span class="hljs-string">&quot;id&quot;</span>,
        <span class="hljs-attr">data_type</span>: <span class="hljs-title class_">DataType</span>.<span class="hljs-property">Int64</span>,
        <span class="hljs-attr">is_primary_key</span>: <span class="hljs-literal">true</span>,
        <span class="hljs-attr">auto_id</span>: <span class="hljs-literal">false</span>
    },
    {
        <span class="hljs-attr">name</span>: <span class="hljs-string">&quot;vector&quot;</span>,
        <span class="hljs-attr">data_type</span>: <span class="hljs-title class_">DataType</span>.<span class="hljs-property">FloatVector</span>,
        <span class="hljs-attr">dim</span>: <span class="hljs-number">5</span>
    },
]

<span class="hljs-comment">// 2.2 Prepare index parameters</span>
<span class="hljs-keyword">const</span> index_params = [{
    <span class="hljs-attr">field_name</span>: <span class="hljs-string">&quot;id&quot;</span>,
    <span class="hljs-attr">index_type</span>: <span class="hljs-string">&quot;STL_SORT&quot;</span>
},{
    <span class="hljs-attr">field_name</span>: <span class="hljs-string">&quot;vector&quot;</span>,
    <span class="hljs-attr">index_type</span>: <span class="hljs-string">&quot;IVF_FLAT&quot;</span>,
    <span class="hljs-attr">metric_type</span>: <span class="hljs-string">&quot;IP&quot;</span>,
    <span class="hljs-attr">params</span>: { <span class="hljs-attr">nlist</span>: <span class="hljs-number">1024</span>}
}]

<span class="hljs-comment">// 2.3 Create a collection with fields and index parameters</span>
res = <span class="hljs-keyword">await</span> client.<span class="hljs-title function_">createCollection</span>({
    <span class="hljs-attr">collection_name</span>: <span class="hljs-string">&quot;test_collection&quot;</span>,
    <span class="hljs-attr">fields</span>: fields, 
    <span class="hljs-attr">index_params</span>: index_params,
    <span class="hljs-attr">enable_dynamic_field</span>: <span class="hljs-literal">true</span>
})

<span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(res.<span class="hljs-property">error_code</span>)

<span class="hljs-comment">// Output</span>
<span class="hljs-comment">// </span>
<span class="hljs-comment">// Success</span>
<span class="hljs-comment">// </span>

res = <span class="hljs-keyword">await</span> client.<span class="hljs-title function_">getLoadState</span>({
    <span class="hljs-attr">collection_name</span>: <span class="hljs-string">&quot;test_collection&quot;</span>,
})  

<span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(res.<span class="hljs-property">state</span>)

<span class="hljs-comment">// Output</span>
<span class="hljs-comment">// </span>
<span class="hljs-comment">// LoadStateLoaded</span>
<span class="hljs-comment">// </span>
<button class="copy-code-btn"></button></code></pre>
<h2 id="Insert-dynamic-data" class="common-anchor-header">插入动态数据<button data-href="#Insert-dynamic-data" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>一旦创建了数据集，就可以开始插入数据，包括插入动态数据到数据集中。</p>
<h3 id="Prepare-data" class="common-anchor-header">准备数据</h3><p>在本节中，您需要准备一些随机生成的数据，以便稍后插入。</p>
<div class="multipleCode">
   <a href="#python">Python </a> <a href="#java">Java</a> <a href="#javascript">Node.js</a></div>
<pre><code translate="no" class="language-python">colors = [<span class="hljs-string">&quot;green&quot;</span>, <span class="hljs-string">&quot;blue&quot;</span>, <span class="hljs-string">&quot;yellow&quot;</span>, <span class="hljs-string">&quot;red&quot;</span>, <span class="hljs-string">&quot;black&quot;</span>, <span class="hljs-string">&quot;white&quot;</span>, <span class="hljs-string">&quot;purple&quot;</span>, <span class="hljs-string">&quot;pink&quot;</span>, <span class="hljs-string">&quot;orange&quot;</span>, <span class="hljs-string">&quot;brown&quot;</span>, <span class="hljs-string">&quot;grey&quot;</span>]
data = []

<span class="hljs-keyword">for</span> i <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(<span class="hljs-number">1000</span>):
    current_color = random.choice(colors)
    current_tag = random.randint(<span class="hljs-number">1000</span>, <span class="hljs-number">9999</span>)
    data.append({
        <span class="hljs-string">&quot;id&quot;</span>: i,
        <span class="hljs-string">&quot;vector&quot;</span>: [ random.uniform(-<span class="hljs-number">1</span>, <span class="hljs-number">1</span>) <span class="hljs-keyword">for</span> _ <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(<span class="hljs-number">5</span>) ],
        <span class="hljs-string">&quot;color&quot;</span>: current_color,
        <span class="hljs-string">&quot;tag&quot;</span>: current_tag,
        <span class="hljs-string">&quot;color_tag&quot;</span>: <span class="hljs-string">f&quot;<span class="hljs-subst">{current_color}</span>_<span class="hljs-subst">{<span class="hljs-built_in">str</span>(current_tag)}</span>&quot;</span>
    })

<span class="hljs-built_in">print</span>(data[<span class="hljs-number">0</span>])
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-java"><span class="hljs-title class_">List</span>&lt;<span class="hljs-title class_">String</span>&gt; colors = <span class="hljs-title class_">Arrays</span>.<span class="hljs-title function_">asList</span>(<span class="hljs-string">&quot;green&quot;</span>, <span class="hljs-string">&quot;blue&quot;</span>, <span class="hljs-string">&quot;yellow&quot;</span>, <span class="hljs-string">&quot;red&quot;</span>, <span class="hljs-string">&quot;black&quot;</span>, <span class="hljs-string">&quot;white&quot;</span>, <span class="hljs-string">&quot;purple&quot;</span>, <span class="hljs-string">&quot;pink&quot;</span>, <span class="hljs-string">&quot;orange&quot;</span>, <span class="hljs-string">&quot;brown&quot;</span>, <span class="hljs-string">&quot;grey&quot;</span>);
<span class="hljs-title class_">List</span>&lt;<span class="hljs-title class_">JSON</span><span class="hljs-built_in">Object</span>&gt; data = <span class="hljs-keyword">new</span> <span class="hljs-title class_">ArrayList</span>&lt;&gt;();

<span class="hljs-keyword">for</span> (int i=<span class="hljs-number">0</span>; i&lt;<span class="hljs-number">1000</span>; i++) {
    <span class="hljs-title class_">Random</span> rand = <span class="hljs-keyword">new</span> <span class="hljs-title class_">Random</span>();
    <span class="hljs-title class_">String</span> current_color = colors.<span class="hljs-title function_">get</span>(rand.<span class="hljs-title function_">nextInt</span>(colors.<span class="hljs-title function_">size</span>()-<span class="hljs-number">1</span>));
    int current_tag = rand.<span class="hljs-title function_">nextInt</span>(<span class="hljs-number">8999</span>) + <span class="hljs-number">1000</span>;
    <span class="hljs-title class_">JSON</span><span class="hljs-built_in">Object</span> row = <span class="hljs-keyword">new</span> <span class="hljs-title class_">JSON</span><span class="hljs-built_in">Object</span>();
    row.<span class="hljs-title function_">put</span>(<span class="hljs-string">&quot;id&quot;</span>, <span class="hljs-title class_">Long</span>.<span class="hljs-title function_">valueOf</span>(i));
    row.<span class="hljs-title function_">put</span>(<span class="hljs-string">&quot;vector&quot;</span>, <span class="hljs-title class_">Arrays</span>.<span class="hljs-title function_">asList</span>(rand.<span class="hljs-title function_">nextFloat</span>(), rand.<span class="hljs-title function_">nextFloat</span>(), rand.<span class="hljs-title function_">nextFloat</span>(), rand.<span class="hljs-title function_">nextFloat</span>(), rand.<span class="hljs-title function_">nextFloat</span>()));
    row.<span class="hljs-title function_">put</span>(<span class="hljs-string">&quot;color&quot;</span>, current_color);
    row.<span class="hljs-title function_">put</span>(<span class="hljs-string">&quot;tag&quot;</span>, current_tag);
    row.<span class="hljs-title function_">put</span>(<span class="hljs-string">&quot;color_tag&quot;</span>, current_color + <span class="hljs-string">&quot;_&quot;</span> + <span class="hljs-title class_">String</span>.<span class="hljs-title function_">valueOf</span>(rand.<span class="hljs-title function_">nextInt</span>(<span class="hljs-number">8999</span>) + <span class="hljs-number">1000</span>));
    data.<span class="hljs-title function_">add</span>(row);
}

<span class="hljs-title class_">System</span>.<span class="hljs-property">out</span>.<span class="hljs-title function_">println</span>(<span class="hljs-title class_">JSON</span><span class="hljs-built_in">Object</span>.<span class="hljs-title function_">toJSON</span>(data.<span class="hljs-title function_">get</span>(<span class="hljs-number">0</span>)));
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-javascript"><span class="hljs-keyword">const</span> colors = [<span class="hljs-string">&quot;green&quot;</span>, <span class="hljs-string">&quot;blue&quot;</span>, <span class="hljs-string">&quot;yellow&quot;</span>, <span class="hljs-string">&quot;red&quot;</span>, <span class="hljs-string">&quot;black&quot;</span>, <span class="hljs-string">&quot;white&quot;</span>, <span class="hljs-string">&quot;purple&quot;</span>, <span class="hljs-string">&quot;pink&quot;</span>, <span class="hljs-string">&quot;orange&quot;</span>, <span class="hljs-string">&quot;brown&quot;</span>, <span class="hljs-string">&quot;grey&quot;</span>]
<span class="hljs-keyword">var</span> data = []

<span class="hljs-keyword">for</span> (<span class="hljs-keyword">let</span> i = <span class="hljs-number">0</span>; i &lt; <span class="hljs-number">1000</span>; i++) {
    <span class="hljs-keyword">const</span> current_color = colors[<span class="hljs-title class_">Math</span>.<span class="hljs-title function_">floor</span>(<span class="hljs-title class_">Math</span>.<span class="hljs-title function_">random</span>() * colors.<span class="hljs-property">length</span>)]
    <span class="hljs-keyword">const</span> current_tag = <span class="hljs-title class_">Math</span>.<span class="hljs-title function_">floor</span>(<span class="hljs-title class_">Math</span>.<span class="hljs-title function_">random</span>() * <span class="hljs-number">8999</span> + <span class="hljs-number">1000</span>)
    data.<span class="hljs-title function_">push</span>({
        <span class="hljs-attr">id</span>: i,
        <span class="hljs-attr">vector</span>: [<span class="hljs-title class_">Math</span>.<span class="hljs-title function_">random</span>(), <span class="hljs-title class_">Math</span>.<span class="hljs-title function_">random</span>(), <span class="hljs-title class_">Math</span>.<span class="hljs-title function_">random</span>(), <span class="hljs-title class_">Math</span>.<span class="hljs-title function_">random</span>(), <span class="hljs-title class_">Math</span>.<span class="hljs-title function_">random</span>()],
        <span class="hljs-attr">color</span>: current_color,
        <span class="hljs-attr">tag</span>: current_tag,
        <span class="hljs-attr">color_tag</span>: <span class="hljs-string">`<span class="hljs-subst">${current_color}</span>_<span class="hljs-subst">${current_tag}</span>`</span>
    })
}

<span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(data[<span class="hljs-number">0</span>])
<button class="copy-code-btn"></button></code></pre>
<p>您可以通过查看第一个条目来查看生成数据的结构。</p>
<pre><code translate="no">{
    <span class="hljs-built_in">id</span>: <span class="hljs-number">0</span>,
    vector: [
        <span class="hljs-number">0.1275656405044483</span>,
        <span class="hljs-number">0.47417858592773277</span>,
        <span class="hljs-number">0.13858264437643286</span>,
        <span class="hljs-number">0.2390904907020377</span>,
        <span class="hljs-number">0.8447862593689635</span>
    ],
    color: <span class="hljs-string">&#x27;blue&#x27;</span>,
    tag: <span class="hljs-number">2064</span>,
    color_tag: <span class="hljs-string">&#x27;blue_2064&#x27;</span>
}
<button class="copy-code-btn"></button></code></pre>
<h3 id="Insert-data" class="common-anchor-header">插入数据</h3><p>然后，您就可以安全地将数据插入到集合中了。</p>
<div class="language-python">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/pymilvus/v2.4.x/MilvusClient/Vector/insert.md"><code translate="no">insert()</code></a>中的</p>
</div>
<div class="language-java">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/java/v2.4.x/v2/Vector/insert.md"><code translate="no">insert()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="language-javascript">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/node/v2.4.x/Vector/insert.md"><code translate="no">insert()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="multipleCode">
   <a href="#python">Python </a> <a href="#java">Java</a> <a href="#javascript">Node.js</a></div>
<pre><code translate="no" class="language-python">res = client.insert(
    collection_name=<span class="hljs-string">&quot;test_collection&quot;</span>,
    data=data,
)

<span class="hljs-built_in">print</span>(res)

<span class="hljs-comment"># Output</span>
<span class="hljs-comment">#</span>
<span class="hljs-comment"># {</span>
<span class="hljs-comment">#     &quot;insert_count&quot;: 1000,</span>
<span class="hljs-comment">#     &quot;ids&quot;: [</span>
<span class="hljs-comment">#         0,</span>
<span class="hljs-comment">#         1,</span>
<span class="hljs-comment">#         2,</span>
<span class="hljs-comment">#         3,</span>
<span class="hljs-comment">#         4,</span>
<span class="hljs-comment">#         5,</span>
<span class="hljs-comment">#         6,</span>
<span class="hljs-comment">#         7,</span>
<span class="hljs-comment">#         8,</span>
<span class="hljs-comment">#         9,</span>
<span class="hljs-comment">#         &quot;(990 more items hidden)&quot;</span>
<span class="hljs-comment">#     ]</span>
<span class="hljs-comment"># }</span>

time.sleep(<span class="hljs-number">5</span>)
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-java"><span class="hljs-comment">// 3.1 Insert data into the collection</span>
<span class="hljs-title class_">InsertReq</span> insertReq = <span class="hljs-title class_">InsertReq</span>.<span class="hljs-title function_">builder</span>()
    .<span class="hljs-title function_">collectionName</span>(<span class="hljs-string">&quot;customized_setup&quot;</span>)
    .<span class="hljs-title function_">data</span>(data)
    .<span class="hljs-title function_">build</span>();

<span class="hljs-title class_">InsertResp</span> insertResp = client.<span class="hljs-title function_">insert</span>(insertReq);

<span class="hljs-title class_">System</span>.<span class="hljs-property">out</span>.<span class="hljs-title function_">println</span>(<span class="hljs-title class_">JSON</span><span class="hljs-built_in">Object</span>.<span class="hljs-title function_">toJSON</span>(insertResp));

<span class="hljs-comment">// Output:</span>
<span class="hljs-comment">// {&quot;insertCnt&quot;: 1000}</span>

<span class="hljs-title class_">Thread</span>.<span class="hljs-title function_">sleep</span>(<span class="hljs-number">5000</span>);
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-javascript">res = <span class="hljs-keyword">await</span> client.<span class="hljs-title function_">insert</span>({
    <span class="hljs-attr">collection_name</span>: <span class="hljs-string">&quot;test_collection&quot;</span>,
    <span class="hljs-attr">data</span>: data,
})

<span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(res.<span class="hljs-property">insert_cnt</span>)

<span class="hljs-comment">// Output</span>
<span class="hljs-comment">// </span>
<span class="hljs-comment">// 1000</span>
<span class="hljs-comment">// </span>

<span class="hljs-keyword">await</span> <span class="hljs-title function_">sleep</span>(<span class="hljs-number">5000</span>)
<button class="copy-code-btn"></button></code></pre>
<h2 id="Search-with-dynamic-fields" class="common-anchor-header">使用动态字段搜索<button data-href="#Search-with-dynamic-fields" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>如果在创建集合时启用了动态字段并插入了非模式定义的字段，则可以在搜索或查询的筛选表达式中使用这些字段，如下所示。</p>
<div class="language-python">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/pymilvus/v2.4.x/MilvusClient/Vector/search.md"><code translate="no">search()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="language-java">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/java/v2.4.x/v2/Vector/search.md"><code translate="no">search()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="language-javascript">
<p>有关参数的更多信息，请参阅 <a href="https://milvus.io/api-reference/node/v2.4.x/Vector/search.md"><code translate="no">search()</code></a>有关参数的更多信息，请参阅 SDK 参考资料中的</p>
</div>
<div class="multipleCode">
   <a href="#python">Python </a> <a href="#java">Java</a> <a href="#javascript">Node.js</a></div>
<pre><code translate="no" class="language-python"><span class="hljs-comment"># 4. Search with dynamic fields</span>
query_vectors = [[<span class="hljs-number">0.3580376395471989</span>, -<span class="hljs-number">0.6023495712049978</span>, <span class="hljs-number">0.18414012509913835</span>, -<span class="hljs-number">0.26286205330961354</span>, <span class="hljs-number">0.9029438446296592</span>]]

res = client.search(
    collection_name=<span class="hljs-string">&quot;test_collection&quot;</span>,
    data=query_vectors,
    <span class="hljs-built_in">filter</span>=<span class="hljs-string">&quot;color in [\&quot;red\&quot;, \&quot;green\&quot;]&quot;</span>,
    search_params={<span class="hljs-string">&quot;metric_type&quot;</span>: <span class="hljs-string">&quot;L2&quot;</span>, <span class="hljs-string">&quot;params&quot;</span>: {<span class="hljs-string">&quot;nprobe&quot;</span>: <span class="hljs-number">10</span>}},
    limit=<span class="hljs-number">3</span>
)

<span class="hljs-built_in">print</span>(res)

<span class="hljs-comment"># Output</span>
<span class="hljs-comment">#</span>
<span class="hljs-comment"># [</span>
<span class="hljs-comment">#     [</span>
<span class="hljs-comment">#         {</span>
<span class="hljs-comment">#             &quot;id&quot;: 863,</span>
<span class="hljs-comment">#             &quot;distance&quot;: 0.188413605093956,</span>
<span class="hljs-comment">#             &quot;entity&quot;: {</span>
<span class="hljs-comment">#                 &quot;id&quot;: 863,</span>
<span class="hljs-comment">#                 &quot;color_tag&quot;: &quot;red_2371&quot;</span>
<span class="hljs-comment">#             }</span>
<span class="hljs-comment">#         },</span>
<span class="hljs-comment">#         {</span>
<span class="hljs-comment">#             &quot;id&quot;: 799,</span>
<span class="hljs-comment">#             &quot;distance&quot;: 0.29188022017478943,</span>
<span class="hljs-comment">#             &quot;entity&quot;: {</span>
<span class="hljs-comment">#                 &quot;id&quot;: 799,</span>
<span class="hljs-comment">#                 &quot;color_tag&quot;: &quot;red_2235&quot;</span>
<span class="hljs-comment">#             }</span>
<span class="hljs-comment">#         },</span>
<span class="hljs-comment">#         {</span>
<span class="hljs-comment">#             &quot;id&quot;: 564,</span>
<span class="hljs-comment">#             &quot;distance&quot;: 0.3492690920829773,</span>
<span class="hljs-comment">#             &quot;entity&quot;: {</span>
<span class="hljs-comment">#                 &quot;id&quot;: 564,</span>
<span class="hljs-comment">#                 &quot;color_tag&quot;: &quot;red_9186&quot;</span>
<span class="hljs-comment">#             }</span>
<span class="hljs-comment">#         }</span>
<span class="hljs-comment">#     ]</span>
<span class="hljs-comment"># ]</span>
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-java"><span class="hljs-comment">// 4. Search with non-schema-defined fields</span>
<span class="hljs-title class_">List</span>&lt;<span class="hljs-title class_">List</span>&lt;<span class="hljs-title class_">Float</span>&gt;&gt; queryVectors = <span class="hljs-title class_">Arrays</span>.<span class="hljs-title function_">asList</span>(<span class="hljs-title class_">Arrays</span>.<span class="hljs-title function_">asList</span>(<span class="hljs-number">0.</span>3580376395471989f, -<span class="hljs-number">0.</span>6023495712049978f, <span class="hljs-number">0.</span>18414012509913835f, -<span class="hljs-number">0.</span>26286205330961354f, <span class="hljs-number">0.</span>9029438446296592f));

<span class="hljs-title class_">SearchReq</span> searchReq = <span class="hljs-title class_">SearchReq</span>.<span class="hljs-title function_">builder</span>()
    .<span class="hljs-title function_">collectionName</span>(<span class="hljs-string">&quot;customized_setup&quot;</span>)
    .<span class="hljs-title function_">data</span>(queryVectors)
    .<span class="hljs-title function_">filter</span>(<span class="hljs-string">&quot;$meta[\&quot;color\&quot;] in [\&quot;red\&quot;, \&quot;green\&quot;]&quot;</span>)
    .<span class="hljs-title function_">outputFields</span>(<span class="hljs-title class_">List</span>.<span class="hljs-title function_">of</span>(<span class="hljs-string">&quot;id&quot;</span>, <span class="hljs-string">&quot;color_tag&quot;</span>))
    .<span class="hljs-title function_">topK</span>(<span class="hljs-number">3</span>)
    .<span class="hljs-title function_">build</span>();

<span class="hljs-title class_">SearchResp</span> searchResp = client.<span class="hljs-title function_">search</span>(searchReq);

<span class="hljs-title class_">System</span>.<span class="hljs-property">out</span>.<span class="hljs-title function_">println</span>(<span class="hljs-title class_">JSON</span><span class="hljs-built_in">Object</span>.<span class="hljs-title function_">toJSON</span>(searchResp));

<span class="hljs-comment">// Output:</span>
<span class="hljs-comment">// {&quot;searchResults&quot;: [[</span>
<span class="hljs-comment">//     {</span>
<span class="hljs-comment">//         &quot;distance&quot;: 1.3159835,</span>
<span class="hljs-comment">//         &quot;id&quot;: 979,</span>
<span class="hljs-comment">//         &quot;entity&quot;: {</span>
<span class="hljs-comment">//             &quot;color_tag&quot;: &quot;red_7155&quot;,</span>
<span class="hljs-comment">//             &quot;id&quot;: 979</span>
<span class="hljs-comment">//         }</span>
<span class="hljs-comment">//     },</span>
<span class="hljs-comment">//     {</span>
<span class="hljs-comment">//         &quot;distance&quot;: 1.0744804,</span>
<span class="hljs-comment">//         &quot;id&quot;: 44,</span>
<span class="hljs-comment">//         &quot;entity&quot;: {</span>
<span class="hljs-comment">//             &quot;color_tag&quot;: &quot;green_8006&quot;,</span>
<span class="hljs-comment">//             &quot;id&quot;: 44</span>
<span class="hljs-comment">//         }</span>
<span class="hljs-comment">//     },</span>
<span class="hljs-comment">//     {</span>
<span class="hljs-comment">//         &quot;distance&quot;: 1.0060014,</span>
<span class="hljs-comment">//         &quot;id&quot;: 617,</span>
<span class="hljs-comment">//         &quot;entity&quot;: {</span>
<span class="hljs-comment">//             &quot;color_tag&quot;: &quot;red_4056&quot;,</span>
<span class="hljs-comment">//             &quot;id&quot;: 617</span>
<span class="hljs-comment">//         }</span>
<span class="hljs-comment">//     }</span>
<span class="hljs-comment">// ]]}</span>
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-javascript"><span class="hljs-comment">// 4. Search with non-schema-defined fields</span>
<span class="hljs-keyword">const</span> query_vectors = [[<span class="hljs-number">0.1</span>, <span class="hljs-number">0.2</span>, <span class="hljs-number">0.3</span>, <span class="hljs-number">0.4</span>, <span class="hljs-number">0.5</span>]]

res = <span class="hljs-keyword">await</span> client.<span class="hljs-title function_">search</span>({
    <span class="hljs-attr">collection_name</span>: <span class="hljs-string">&quot;test_collection&quot;</span>,
    <span class="hljs-attr">data</span>: query_vectors,
    <span class="hljs-attr">filter</span>: <span class="hljs-string">&quot;color in [\&quot;red\&quot;, \&quot;green\&quot;]&quot;</span>,
    <span class="hljs-attr">output_fields</span>: [<span class="hljs-string">&quot;color_tag&quot;</span>],
    <span class="hljs-attr">limit</span>: <span class="hljs-number">3</span>
})

<span class="hljs-variable language_">console</span>.<span class="hljs-title function_">log</span>(res.<span class="hljs-property">results</span>)

<span class="hljs-comment">// Output</span>
<span class="hljs-comment">// </span>
<span class="hljs-comment">// [</span>
<span class="hljs-comment">//   { score: 1.2284551858901978, id: &#x27;301&#x27;, color_tag: &#x27;red_1270&#x27; },</span>
<span class="hljs-comment">//   { score: 1.2195171117782593, id: &#x27;205&#x27;, color_tag: &#x27;red_2780&#x27; },</span>
<span class="hljs-comment">//   { score: 1.2055039405822754, id: &#x27;487&#x27;, color_tag: &#x27;red_6653&#x27; }</span>
<span class="hljs-comment">// ]</span>
<span class="hljs-comment">// </span>
<button class="copy-code-btn"></button></code></pre>
<h2 id="Recaps" class="common-anchor-header">重述<button data-href="#Recaps" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>值得注意的是，<strong>color</strong>、<strong>tag</strong>和<strong>color_tag</strong>在定义集合模式时并不存在，但您可以在进行搜索和查询时将它们用作模式定义的字段。</p>
<p>如果非模式定义字段的名称包含除数字、字母和下划线以外的字符，如加号 (+)、星号 (*) 或美元符号 ($)，则在布尔表达式中使用该字段或将其包含在输出字段中时，必须将该键包含在<strong>$meta[]</strong>中，如以下代码片段所示。</p>
<pre><code translate="no" class="language-python"><span class="hljs-meta">... </span>
<span class="hljs-built_in">filter</span>=<span class="hljs-string">&#x27;$meta[&quot;$key&quot;] in [&quot;a&quot;, &quot;b&quot;, &quot;c&quot;]&#x27;</span>, 
output_fields=<span class="hljs-string">&#x27;$meta[&quot;$key&quot;]&#x27;</span>  
...
<button class="copy-code-btn"></button></code></pre>