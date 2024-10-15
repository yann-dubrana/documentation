---

<h1 id="yaaps-api-yet-another-apps">Yaaps API (Yet Another Apps)</h1>
<h2 id="project-overview">Project Overview</h2>
<p>Yaaps API is a geographic data API that aggregates and provides access to a wide range of open-source<br>
datasets focused on France. By combining data primarily from <a href="https://www.data.gouv.fr/fr/">data.gouv.fr</a> and other<br>
authoritative sources, it offers detailed geographic information layers for maps. The core concept behind Yaaps API is<br>
to enable the contextualization of customers’ private data within powerful web applications by leveraging the<br>
open-source data that Yaaps provide.</p>
<h3 id="features">Features</h3>
<ul>
<li><strong>FastAPI-Driven</strong>: Leveraging <a href="https://fastapi.tiangolo.com/">FastAPI</a> for high performance, easy to code , and<br>
automatic OpenAPI documentation.</li>
<li><strong>Advanced Security</strong>: Utilizes <a href="https://docs.logto.io/">Logto</a> for authentication and authorization, integrated using<br>
FastAPI’s native security<br>
features.</li>
<li><strong>SQLModel Integration</strong>: Database interactions are streamlined using <a href="https://sqlmodel.tiangolo.com/">SQLModel</a>,<br>
providing an intuitive interface<br>
between your database and API. Write by FastAPI developer, based<br>
on <a href="https://docs.pydantic.dev/latest/">Pydantic</a> &amp; <a href="https://docs.sqlalchemy.org/en/20/">SQLAlchemy</a>, integration is<br>
flawless.</li>
<li><strong>Redis Caching</strong>: Implements <a href="https://github.com/long2ice/fastapi-cache">Redis with fastapi-cache2</a> for efficient<br>
caching, significantly improving response times for frequent<br>
queries.</li>
<li><strong>Auto-generated Documentation</strong>: Comprehensive API documentation is automatically generated, making it easy for<br>
developers to understand and use the API, based on strong Pydantic/SQLModel object declaration. Better the code,<br>
Better the doc.</li>
<li><strong>Geographic Layer Support</strong>: Automatic support for tiles generation and geometric/geographic queries on database<br>
tables with postgis columns. Using <a href="https://geoalchemy-2.readthedocs.io/en/latest/index.html">GeoAlchemy</a> to implement<br>
all postgis function with SQLModel</li>
<li><strong>Flexible Data Handling</strong>: While primarily focused on geographic data, the API can handle and serve any type of data<br>
stored in PostgreSQL tables.</li>
<li><strong>Rapid Complex Endpoint Creation</strong>: Easily create API endpoints for any PostgreSQL table, with special support for<br>
PostGIS geographic data. You can integrate new data in your API in no time.</li>
<li><strong>High Flexibility</strong>: Even if the modules provides all the basic function, you can add more complex use case either in<br>
models object and / or routers. Api is flexible enough for most usecase.</li>
</ul>
<p>Yaaps API processes and standardizes geographic data, making it easily accessible for integration into web applications<br>
and client custom modules. This standardization ensures that the contextualization of private data with open data is<br>
smooth and efficient, allowing for the creation of powerful, data-driven applications.</p>
<p>By providing this rich set of features and data sources, Yaaps API enables clients to build sophisticated applications<br>
that leverage the power of both their proprietary data and the vast landscape of open data, creating unique insights and<br>
value for their users.</p>
<h2 id="current-data-sources">Current Data Sources</h2>
<ul>
<li><a href="https://www.data.gouv.fr/fr/datasets/base-de-donnees-nationale-des-batiments/">National Building Database</a></li>
<li><a href="https://odre.opendatasoft.com/">Electrical Networks, Gas, Distribution Stations</a></li>
<li><a href="https://www.data.gouv.fr/fr/datasets/fichier-consolide-des-bornes-de-recharge-pour-vehicules-electriques/">Vehicles - Charging Stations</a></li>
<li><a href="https://data.ademe.fr/applications/sites-pollues-(test)">Pollution - ADEME Polluted Sites</a></li>
<li><a href="https://cartefibre.arcep.fr/index.html?lng=2.9155336656537543&amp;lat=46&amp;zoom=6.5&amp;mode=normal&amp;legende=true&amp;filter=true&amp;trimestre=2024T2">Telephone and Internet Networks</a></li>
</ul>
<p><strong>Note:</strong> These links may not represent the best data sources. For optimal sources, consult Eleonore, who has<br>
comprehensive knowledge of the best data sources.</p>
<h3 id="data-integration-process">Data Integration Process</h3>
<ol>
<li>Create a schema in the YAAPS database organized by major data type families.</li>
<li>Import data using various tools:
<ul>
<li>pgrestore for pgdump type</li>
<li>QGIS or Geopandas in Python for others (QGIS do it automatically but is not really stable, Geopandas is good but<br>
you need to write the import script)</li>
</ul>
</li>
</ol>
<p><strong>Note :</strong> Benjamin should implement a Geographic ETL upon arrival to ensure automatic data updates. We think<br>
about <a href="https://fme.safe.com/fme-in-action/data-types/">FME</a></p>
<h3 id="data-format">Data Format</h3>
<p>Data is integrated in its original format, often in French, to:</p>
<ul>
<li>Facilitate updates</li>
<li>Maintain a common reference for all current users of these databases</li>
</ul>
<p><strong>Note:</strong> Choice of simplicity in deadline context, we need to discuss this point more.</p>
<h2 id="requirements">Requirements</h2>
<p>To run the Yaaps API, ensure that you have the following dependencies installed:</p>
<ul>
<li><strong>FastAPI (v0.115.2)</strong>: A modern, high-performance web framework for building APIs with Python, using standard Python<br>
type hints. It also provides automatic OpenAPI documentation generation.</li>
<li><strong>fastapi_cache (v0.1.0)</strong>: A caching extension for FastAPI, allowing for efficient query caching using Redis.</li>
<li><strong>GeoAlchemy2 (v0.15.2)</strong>: Adds spatial support to SQLAlchemy, enabling the use of geographic and geometric data types<br>
in PostgreSQL via PostGIS.</li>
<li><strong>geojson (v3.1.0)</strong>: A Python library for manipulating GeoJSON data formats, widely used for representing<br>
geographical features.</li>
<li><strong>Pydantic (v2.9.2)</strong>: A data validation and settings management library, used for creating data models with type<br>
checking and serialization in FastAPI.</li>
<li><strong>pydantic_geojson (v0.1.1)</strong>: Extends Pydantic to include GeoJSON format support, enabling seamless handling of<br>
geographical data models.</li>
<li><strong>pydantic_settings (v2.5.2)</strong>: A configuration management extension for Pydantic, simplifying environment-based<br>
settings for the API.</li>
<li><strong>python-jose (v3.3.0)</strong>: A JavaScript Object Signing and Encryption (JOSE) implementation in Python, used for<br>
handling JWT tokens in the authentication process.</li>
<li><strong>Shapely (v2.0.6)</strong>: A library for geometric operations, used to create and manipulate geometries such as points,<br>
lines, and polygons.</li>
<li><strong>SQLAlchemy (v2.0.31)</strong>: The core SQL toolkit and Object-Relational Mapping (ORM) library for Python, used for<br>
handling database interactions.</li>
<li><strong>SQLModel (v0.0.22)</strong>: An ORM built on top of SQLAlchemy and Pydantic, providing an intuitive way to define and query<br>
database models in FastAPI.</li>
<li><strong>sshtunnel (v0.4.0)</strong>: A Python module that allows the establishment of SSH tunnels, useful for securely connecting<br>
to remote databases.</li>
</ul>
<h3 id="must-know">Must Know</h3>
<h4 id="fastapi-custom-swagger-documentation">FastAPI Custom Swagger Documentation</h4>
<p>The FastAPI documentation in this project uses a custom Swagger UI, which is located at <code>static/swagger-ui-bundle.js</code>.<br>
This custom build introduces a new resource argument to the native OAuth authentication system, making it compatible<br>
with the Logto authentication system.</p>
<p>You can find the custom Swagger UI fork on GitHub<br>
here: <a href="https://github.com/yann-dubrana/swagger-ui">yann-dubrana/swagger-ui</a>.</p>
<h4 id="fastapi-cache-customization">FastAPI-Cache Customization</h4>
<p>The project uses a modified version of <code>fastapi_cache</code> hosted<br>
at <a href="https://github.com/yann-dubrana/fastapi-cache">yann-dubrana/fastapi-cache</a>. This is a clone of the<br>
original <code>fastapi-cache</code> repository by <a href="https://github.com/long2ice/fastapi-cache">long2ice</a>, with an additional pull<br>
request (PR) based on contributions from <strong>hozn</strong> (#283).</p>
<p>The modification allows copying headers if a custom encoder returns an instance of a Starlette response, making it<br>
possible to cache binary data while preserving FastAPI cache headers. This is particularly important for caching Mapbox<br>
Vector Tiles (MVT) for improved performance.</p>
<h2 id="installation">Installation</h2>
<p>To set up the Yaaps API for development using <strong>PyCharm</strong> on Windows, follow these steps:</p>
<h3 id="step-1-clone-the-repository">Step 1: Clone the Repository</h3>
<p>Start by cloning the Yaaps API repository:</p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">git</span> clone <span class="token operator">&lt;</span>repository-url<span class="token operator">&gt;</span>cd <span class="token operator">&lt;</span>repository-folder<span class="token operator">&gt;</span>```  
  
<span class="token comment">### Step 2: Set Up a Virtual Environment  </span>
  
In **PyCharm**:  
  
1. Open **PyCharm** and <span class="token keyword">select</span> **Open** to <span class="token function">open</span> the cloned project folder.  
2. Navigate to **File** <span class="token operator">&gt;</span> **Settings** <span class="token operator">&gt;</span> **Project: <span class="token operator">&lt;</span>project_name<span class="token operator">&gt;</span>** <span class="token operator">&gt;</span> **Python Interpreter**.  
3. Click the gear icon and <span class="token keyword">select</span> **Add** <span class="token operator">&gt;</span> **Virtualenv Environment**.  
4. Choose **New Environment**, specify a location <span class="token punctuation">(</span>e.g., <span class="token variable"><span class="token variable">`</span>venv<span class="token variable">`</span></span> folder<span class="token punctuation">)</span>, and <span class="token keyword">set</span> the Python version <span class="token punctuation">(</span>3.8+<span class="token punctuation">)</span>.  
  
Alternatively, create it manually via the terminal:  
  
```bash  
python -m venv venvvenv\Scripts\activate <span class="token comment"># Activate in Windows```  </span>
  
<span class="token comment">### Step 3: Install Dependencies  </span>
  
Once the virtual environment is activated, <span class="token function">install</span> the dependencies:  
  
``<span class="token variable"><span class="token variable">`</span><span class="token function">bash</span>  
pip <span class="token function">install</span> -r requirements.txt<span class="token variable">`</span></span>``  
  
<span class="token comment">### Step 4: Configure Environment Variables  </span>
  
Create a <span class="token variable"><span class="token variable">`</span>.env<span class="token variable">`</span></span> <span class="token function">file</span> <span class="token keyword">in</span> the root of your project and add the following environment variables:  
  
</code></pre>
<h1 id="authentication-configuration">Authentication Configuration</h1>
<p>AUTHENTICATION__TOKEN_URL=https://example.com/oauth/token<br>
AUTHENTICATION__AUTHORIZATION_URL=https://example.com/oauth/authorize<br>
AUTHENTICATION__JWKS_URI=https://example.com/.well-known/jwks.json<br>
AUTHENTICATION__ISSUER=https://example.com<br>
AUTHENTICATION__RESOURCE=https://example.com/resource<br>
AUTHENTICATION__CLIENT_ID=your-client-id<br>
AUTHENTICATION__CLIENT_SECRET=your-client-secret<br>
AUTHENTICATION__SCOPES=your-scopes</p>
<h1 id="documentation-configuration">Documentation Configuration</h1>
<p>DOCUMENTATION__JS_URL=https://example.com/docs.js<br>
DOCUMENTATION__FAVICON_URL=https://example.com/favicon.ico<br>
DOCUMENTATION__PERSIST_AUTHORIZATION=false</p>
<h1 id="redis-configuration">Redis Configuration</h1>
<p>REDIS__URL=redis://localhost:6379/0<br>
REDIS__PREFIX=your-prefix</p>
<h1 id="database-configuration">Database Configuration</h1>
<p>DATABASE__PROVIDER=postgresql<br>
DATABASE__DIALECT=psycopg2<br>
DATABASE__USER=your-database-user<br>
DATABASE__PASSWORD=your-database-password<br>
DATABASE__HOST=localhost<br>
DATABASE__PORT=5432<br>
DATABASE__DATABASE=your-database-name<br>
DATABASE__ECHO=false</p>
<h1 id="database-proxy-configuration">Database Proxy Configuration</h1>
<p>DATABASE__PROXY__ENABLED=false<br>
DATABASE__PROXY__HOST=proxy-host<br>
DATABASE__PROXY__USER=proxy-user<br>
DATABASE__PROXY__PASSWORD=proxy-password<br>
DATABASE__PROXY__REMOTE_HOST=remote-host<br>
DATABASE__PROXY__REMOTE_PORT=remote-port</p>
<h1 id="openapi-configuration">OpenAPI Configuration</h1>
<p>OPENAPI_URL=/openapi.json<br>
TITLE=API<br>
FRONTEND_URL=[“<a href="http://localhost:3000">http://localhost:3000</a>”,“<a href="http://localhost:8000">http://localhost:8000</a>”]</p>
<pre><code>  
These environment variables are automatically loaded into a Pydantic ApiSettings object. All class settings linked to  
the .env file are defined in modules/settings. The double underscore (__) in variable names indicates the nested  
structure of properties in the object for Pydantic's autoloading. For example, DATABASE__PROXY__ENABLED corresponds to  
the enabled boolean member of the ProxySettings class, which itself is a member of the DatabaseSettings class. Finally,  
database is the member of the top-level ApiSettings class.  
  
**Note:** You can create the .env file with the data in passbolt but this quite complex. First time call Yann.  
  
### Step 5: Run the API  
  
You have two options to run the API:  
  
1. **Create a PyCharm Run Configuration**:  
  
   - In **PyCharm**, go to **Run** &gt; **Edit Configurations**.  
   - Click the `+` button to add a new **Python** configuration.  
   - Set the script path to your main application file (e.g., `app/main.py`).  
   - Set the working directory to your project folder.  
   - Click **Apply** and **OK**.  
   - Now, you can run the API directly from the PyCharm toolbar using the green play button.  
  
2. **Run the API using Uvicorn from the terminal**:  
  
   If you prefer to use the terminal, you can run the API with Uvicorn:  
  
   ```bash  
  uvicorn app.main:app --reload ```  
  This will start the development server on `http://127.0.0.1:8000`.  
  
### Step 6: Access the API Documentation  
  
With the server running, access the API documentation at:  
  
- **Swagger UI**: `http://127.0.0.1:8000/docs`  
- **Redoc**: `http://127.0.0.1:8000/redoc`  
  
## Modules  
  
### Database  
  
#### Manager  
  
The `DatabaseManager` submodule handles database connection management and session creation. It uses **SQLModel** to  
connect to a PostgreSQL database and optionally supports an SSH tunnel through the **ProxyManager**.  
  
##### Key Components  
  
###### `DatabaseManager` Class  
  
- **Connection Management**: Establishes the database connection using the settings provided in the `.env` file ( see  
  Step 4: Configure Environment Variables on how settins module work). It  
  validates the configuration to ensure that PostgreSQL with the `psycopg2` dialect is used.  
- **Session Management**: Provides methods for generating sessions to interact with the database.  
- **Database Initialization**: Offers a method to create the database schema using SQLModel. We don't use it know, but  
  the idea is to be able to create an empty database from SQLModel, or change some columns. Ideally, Database migration  
  tools we'll be needed if ETL project is not conclusive.  
- **Proxy Integration**: Integrates the `ProxyManager` to support SSH tunnels for database connections when necessary.  
  Usefull to connect to servers database when you can't recreate local database because data size.  
  
###### `ProxyManager` Class  
  
- Manages an optional SSH tunnel for the database connection, based on the proxy settings in the `.env` file.  
- Provides methods to start and stop the SSH tunnel.  
  
##### How It Works  
  
1. **Database Connection**: The `DatabaseManager` sets up the connection based on the `.env` file, ensuring a valid  
   configuration for PostgreSQL.  
2. **Session Handling**: Sessions are created and used for database interactions. Sessions are well integrated with  
   FastAPI dependencies injection.  
3. **SSH Tunnel (Optional)**: If proxy settings are enabled, the `ProxyManager` establishes an SSH tunnel for secure  
   access to the database.  
  
#### Templates Module  
  
The **Templates Module** provides abstract classes that streamline CRUD operations and geometry-based queries for  
database models in applications using `SQLModel` and `SQLAlchemy`. This module also includes support for spatial queries  
on geometric data, making it ideal for applications that manage geographic information. Idea is to use Composition  
pattern (multiple heritage) to add some functions to a Database class. An Commune(SQLModelCrud, table=true) have crud  
class method automatically implemented. if you ass SQLModelTiles, class method get_tile to generate mvt tiles is added.  
  
##### Key Components  
  
###### `SQLModelCRUD` Class  
  
- **Basic CRUD Operations**: Implements common database operations like `get`, `create`, `update`, and `delete`.  
- **Session-Based**: All operations are executed within a provided SQLAlchemy `Session`.  
  
###### `SQLModelGeometry` Class  
  
- **Spatial Queries**: Extends the `SQLModelCRUD` class to handle spatial data using GeoAlchemy2 functions.  
- **Geometry Properties**: Provides properties to access and manipulate geographic data (  
  e.g., `longitude`, `latitude`, `coords`).  
- **Boundary Queries**: Supports querying data within geographic boundaries or from a specific point.  
  
###### `SQLModelTile` Class  
  
- **Map Tile Queries**: Supports vector tile generation for geographic data, leveraging `ST_AsMVT` and other PostGIS  
  functions.  
- **TileQueryBuilder**: Builds efficient queries to retrieve geographic data for specific map tiles using the z/x/y  
  coordinates and returns the data in vector tile format.  
  
##### How It Works  
  
- **CRUD Operations**: The `SQLModelCRUD` class provides base methods for interacting with the database, abstracting  
  repetitive CRUD logic.  
- **Geometry Handling**: The `SQLModelGeometry` class enables spatial data handling, such as querying based on  
  geographic boundaries or specific coordinates.  
- **Tile Generation**: The `SQLModelTile` class provides a way to generate map tiles (vector tiles) from geographic  
  data, making it suitable for applications that need to display map-based data efficiently.  
  
This module simplifies the interaction with the database and geographic data by providing reusable templates for common  
operations.  
  
#### Types Module  
  
The **Types Module** defines custom types used to handle geographic data in the database. The key component is  
the `FeatureModelGeometry` class, which extends SQLAlchemy's `Geometry` type to seamlessly work with PostGIS and  
GeoJSON, enabling direct conversion of geometric objects into GeoJSON format without needing additional Python-side  
processing.  
  
##### Key Component  
  
###### `FeatureModelGeometry` Class  
  
- **Custom Geometry Type**: A custom SQLAlchemy `TypeDecorator` that extends the `Geometry` type from `GeoAlchemy2`.  
- **GeoJSON Conversion**: Automatically converts PostGIS geometry objects to GeoJSON format directly in SQL queries,  
  reducing overhead and making it easier to handle geographic data in web applications.  
- **SRID Transformation**: Supports spatial reference system transformation using PostGIS's `ST_Transform` function. The  
  default output SRID is set to 4326 (WGS 84), but it can be customized as needed.  
- **Database Integration**: Handles both the serialization and deserialization of geometric data, converting input  
  GeoJSON data into PostGIS geometry format and converting the result back to GeoJSON.  
  
##### How It Works  
  
All these methods are used by SQLAlchemy to construct queries.  
  
- **Column Expression**: The `column_expression` method transforms the geometric data to the target SRID and converts it  
  to GeoJSON using the PostGIS `ST_AsGeoJSON` function. The result is a JSON object structured as a GeoJSON Feature.  
- **Bind Parameter**: The `process_bind_param` method converts GeoJSON geometry data into a format compatible with  
  PostGIS when saving data into the database.  
- **Bind Expression**: The `bind_expression` method transforms GeoJSON into PostGIS geometry using `ST_GeomFromGeoJSON`,  
  enabling seamless storage of spatial data.  
  
#### GeoJSON Processor Module  
  
The **GeoJSON Processor Module** converts database items with geometric data into GeoJSON format or returns raw data  
based on the specified output type (GeoJSON or plain). It ensures seamless integration of geographic information for web  
applications and mapping tools.  
  
### Database model creation  
  
#### Overview  
  
After you create the table in the database, in the corresponding schema module, create a python file.  
  
##### 1. Define the Base Model  
  
Start by creating a base model using Pydantic. This model will define the attributes that will be mapped to the database  
table.  
  
```python  
from pydantic import BaseModel, Field  
  
  
class NewModelBase(BaseModel):  
 attribute_one: str = Field(description="Description of attribute one") attribute_two: Optional[int] = Field(description="Description of attribute two")  
</code></pre>
<h5 id="create-feature-properties-class">2. Create Feature Properties Class</h5>
<p>If your model requires GeoJSON representation, create a properties class that extends the base model. This class will<br>
include properties specific to GeoJSON.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">class</span> <span class="token class-name">NewModelFeatureProperties</span><span class="token punctuation">(</span>NewModelBase<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 <span class="token keyword">pass</span>  
</code></pre>
<h5 id="define-the-feature-model">3. Define the Feature Model</h5>
<p>Create a feature model that specifies the geometry and properties. Use appropriate geometric types, such<br>
as <code>MultiPolygonModel</code> for geographic data.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> pydantic_geojson <span class="token keyword">import</span> FeatureModel  
<span class="token keyword">from</span> pydantic_geojson <span class="token keyword">import</span> MultiPolygonModel  
  
  
<span class="token keyword">class</span> <span class="token class-name">NewModelFeature</span><span class="token punctuation">(</span>FeatureModel<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 geometry<span class="token punctuation">:</span> MultiPolygonModel <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Geometry of the new model"</span><span class="token punctuation">)</span> properties<span class="token punctuation">:</span> NewModelFeatureProperties <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Properties of the new model"</span><span class="token punctuation">)</span>  
</code></pre>
<h5 id="create-a-feature-collection-class">4. Create a Feature Collection Class</h5>
<p>If your model will represent a collection of features, define a feature collection class.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> pydantic_geojson <span class="token keyword">import</span> FeatureCollectionModel  
  
  
<span class="token keyword">class</span> <span class="token class-name">NewModelFeatureCollection</span><span class="token punctuation">(</span>FeatureCollectionModel<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 features<span class="token punctuation">:</span> List<span class="token punctuation">[</span>NewModelFeature<span class="token punctuation">]</span> <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Collection of new model features"</span><span class="token punctuation">)</span>  
</code></pre>
<h5 id="define-the-sqlmodel-class">5. Define the SQLModel Class</h5>
<p>Create a class for your model that inherits from SQLModel and any other relevant classes for geographic functionality.<br>
Include table arguments, relationships, and column definitions.</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> sqlmodel <span class="token keyword">import</span> SQLModel<span class="token punctuation">,</span> Field<span class="token punctuation">,</span> Relationship  
<span class="token keyword">from</span> sqlalchemy <span class="token keyword">import</span> Column<span class="token punctuation">,</span> ForeignKeyConstraint<span class="token punctuation">,</span> Index<span class="token punctuation">,</span> PrimaryKeyConstraint  
  
  
<span class="token keyword">class</span> <span class="token class-name">NewModel</span><span class="token punctuation">(</span>NewModelBase<span class="token punctuation">,</span> SQLModelGeometry<span class="token punctuation">,</span> SQLModelTile<span class="token punctuation">,</span> SQLModel<span class="token punctuation">,</span> table<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span><span class="token punctuation">:</span>  
 __table_args__ <span class="token operator">=</span> <span class="token punctuation">(</span> ForeignKeyConstraint<span class="token punctuation">(</span> columns<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">'foreign_key_attribute'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> refcolumns<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">'related_table.primary_key'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> name<span class="token operator">=</span><span class="token string">'new_model_foreign_key_fkey'</span> <span class="token punctuation">)</span><span class="token punctuation">,</span> PrimaryKeyConstraint<span class="token punctuation">(</span><span class="token string">'primary_key_attribute'</span><span class="token punctuation">,</span> name<span class="token operator">=</span><span class="token string">'new_model_pkey'</span><span class="token punctuation">)</span><span class="token punctuation">,</span> Index<span class="token punctuation">(</span><span class="token string">'new_model_index_name'</span><span class="token punctuation">,</span> <span class="token string">'attribute_one'</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">'comment'</span><span class="token punctuation">:</span> <span class="token string">"Comment describing the new model"</span><span class="token punctuation">}</span> <span class="token punctuation">)</span>  
 <span class="token comment"># Define additional geometric fields geom_attribute: FeatureModel = Field( sa_column=Column( 'geom_attribute', FeatureModelGeometry(output_srid=4326), comment='Geometric attribute of the new model' ) )  </span>
 <span class="token comment"># Define relationships to other models related_model: Optional['RelatedModel'] = Relationship(back_populates='new_model')  </span>
</code></pre>
<h5 id="implement-properties-and-methods">6. Implement Properties and Methods</h5>
<p>Define any properties or methods necessary for your model. These can be used for computed values or to simplify access<br>
to properties.</p>
<pre class=" language-python"><code class="prism  language-python">@<span class="token builtin">property</span>  
<span class="token keyword">def</span> <span class="token function">id</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 <span class="token keyword">return</span> self<span class="token punctuation">.</span>primary_key_attribute  
  
@<span class="token builtin">property</span>  
<span class="token keyword">def</span> <span class="token function">properties</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> NewModelFeatureProperties<span class="token punctuation">:</span>  
 <span class="token keyword">return</span> NewModelFeatureProperties<span class="token punctuation">(</span><span class="token operator">**</span><span class="token builtin">super</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span>properties<span class="token punctuation">)</span>  
</code></pre>
<h5 id="example-creating-a-new-model">Example: Creating a New Model</h5>
<p>Here’s a complete example of how a new model can be defined using the steps outlined above:</p>
<pre class=" language-python"><code class="prism  language-python"><span class="token keyword">from</span> typing <span class="token keyword">import</span> List<span class="token punctuation">,</span> Optional  
<span class="token keyword">from</span> pydantic <span class="token keyword">import</span> BaseModel<span class="token punctuation">,</span> Field  
<span class="token keyword">from</span> pydantic_geojson <span class="token keyword">import</span> FeatureCollectionModel<span class="token punctuation">,</span> MultiPolygonModel<span class="token punctuation">,</span> FeatureModel  
<span class="token keyword">from</span> sqlmodel <span class="token keyword">import</span> SQLModel<span class="token punctuation">,</span> Field<span class="token punctuation">,</span> Relationship  
<span class="token keyword">from</span> sqlalchemy <span class="token keyword">import</span> Column<span class="token punctuation">,</span> ForeignKeyConstraint<span class="token punctuation">,</span> Index<span class="token punctuation">,</span> PrimaryKeyConstraint  
  
  
<span class="token keyword">class</span> <span class="token class-name">ParkBase</span><span class="token punctuation">(</span>BaseModel<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 park_name<span class="token punctuation">:</span> <span class="token builtin">str</span> <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Name of the park"</span><span class="token punctuation">)</span> area_size<span class="token punctuation">:</span> <span class="token builtin">float</span> <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Area size of the park in hectares"</span><span class="token punctuation">)</span>  
  
<span class="token keyword">class</span> <span class="token class-name">ParkFeatureProperties</span><span class="token punctuation">(</span>ParkBase<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 <span class="token keyword">pass</span>  
  
<span class="token keyword">class</span> <span class="token class-name">ParkFeature</span><span class="token punctuation">(</span>FeatureModel<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 geometry<span class="token punctuation">:</span> MultiPolygonModel <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Geometry of the park"</span><span class="token punctuation">)</span> properties<span class="token punctuation">:</span> ParkFeatureProperties <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Properties of the park"</span><span class="token punctuation">)</span>  
  
<span class="token keyword">class</span> <span class="token class-name">ParkFeatureCollection</span><span class="token punctuation">(</span>FeatureCollectionModel<span class="token punctuation">)</span><span class="token punctuation">:</span>  
 features<span class="token punctuation">:</span> List<span class="token punctuation">[</span>ParkFeature<span class="token punctuation">]</span> <span class="token operator">=</span> Field<span class="token punctuation">(</span>description<span class="token operator">=</span><span class="token string">"Collection of park features"</span><span class="token punctuation">)</span>  
  
<span class="token keyword">class</span> <span class="token class-name">Park</span><span class="token punctuation">(</span>ParkBase<span class="token punctuation">,</span> SQLModelGeometry<span class="token punctuation">,</span> SQLModelTile<span class="token punctuation">,</span> SQLModel<span class="token punctuation">,</span> table<span class="token operator">=</span><span class="token boolean">True</span><span class="token punctuation">)</span><span class="token punctuation">:</span>  
 __table_args__ <span class="token operator">=</span> <span class="token punctuation">(</span> ForeignKeyConstraint<span class="token punctuation">(</span> columns<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">'department_id'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> refcolumns<span class="token operator">=</span><span class="token punctuation">[</span><span class="token string">'department.id'</span><span class="token punctuation">]</span><span class="token punctuation">,</span> name<span class="token operator">=</span><span class="token string">'park_department_fkey'</span> <span class="token punctuation">)</span><span class="token punctuation">,</span> PrimaryKeyConstraint<span class="token punctuation">(</span><span class="token string">'id'</span><span class="token punctuation">,</span> name<span class="token operator">=</span><span class="token string">'park_pkey'</span><span class="token punctuation">)</span><span class="token punctuation">,</span> Index<span class="token punctuation">(</span><span class="token string">'park_name_idx'</span><span class="token punctuation">,</span> <span class="token string">'park_name'</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token punctuation">{</span><span class="token string">'comment'</span><span class="token punctuation">:</span> <span class="token string">"Information about parks in the region"</span><span class="token punctuation">}</span> <span class="token punctuation">)</span>  
 geom_park<span class="token punctuation">:</span> FeatureModel <span class="token operator">=</span> Field<span class="token punctuation">(</span> sa_column<span class="token operator">=</span>Column<span class="token punctuation">(</span> <span class="token string">'geom_park'</span><span class="token punctuation">,</span> FeatureModelGeometry<span class="token punctuation">(</span>output_srid<span class="token operator">=</span><span class="token number">4326</span><span class="token punctuation">)</span><span class="token punctuation">,</span> comment<span class="token operator">=</span><span class="token string">'Geometric representation of the park'</span> <span class="token punctuation">)</span> <span class="token punctuation">)</span>  
 department<span class="token punctuation">:</span> Optional<span class="token punctuation">[</span><span class="token string">'Department'</span><span class="token punctuation">]</span> <span class="token operator">=</span> Relationship<span class="token punctuation">(</span>back_populates<span class="token operator">=</span><span class="token string">'parks'</span><span class="token punctuation">)</span>  
 @<span class="token builtin">property</span> <span class="token keyword">def</span> <span class="token function">id</span><span class="token punctuation">(</span>self<span class="token punctuation">)</span><span class="token punctuation">:</span> <span class="token keyword">return</span> self<span class="token punctuation">.</span><span class="token builtin">id</span>  
</code></pre>
<p>By following these steps, you can create class that represents table in your database and incorporate powerfull<br>
geographic functionalities. The modular design allows for flexibility and reusability, enabling the development of<br>
sophisticated data models tailored to your application’s needs.</p>
<h3 id="cache">Cache</h3>
<p>[Information about any caching mechanisms employed]</p>
<h3 id="security">Security</h3>
<p>[Overview of security measures and authentication processes]</p>
<h3 id="routing">Routing</h3>
<p>[Explanation of the API’s routing system]</p>
<h3 id="documentation">Documentation</h3>
<p>[Information about where to find detailed API documentation]</p>
<h2 id="api-endpoints">API Endpoints</h2>
<p>Yaaps API provides a wide range of endpoints across different schemas. Here’s a high-level overview of the main endpoint<br>
groups:</p>
<ul>
<li><code>/bdnb-administratif/</code>: Endpoints for administrative divisions (communes, départements, regions, IRIS)</li>
<li><code>/bdnb/</code>: Endpoints for national building database, including addresses, buildings, parcels, and related data</li>
<li><code>/energies/</code>: Endpoints for energy distribution networks and infrastructure</li>
<li><code>/irve/</code>: Endpoints for electric vehicle charging stations</li>
<li><code>/pollutions/</code>: Endpoints for pollution data, including ADEME soil pollution sites</li>
<li><code>/reseaux/</code>: Endpoints for network infrastructure, including mobile bases and internet coverage</li>
</ul>
<p>Each group contains multiple endpoints for retrieving data by ID, within boundaries, and as vector tiles.</p>
<h2 id="usage-examples">Usage Examples</h2>
<p>[Placeholder for code examples demonstrating how to use key API endpoints]</p>
<h2 id="testing">Testing</h2>
<p>[Placeholder for information about running tests]</p>
<h2 id="deployment">Deployment</h2>
<p>[Placeholder for deployment instructions]</p>
<p>For more detailed information about specific endpoints and data structures, please refer to our full API documentation.</p>

