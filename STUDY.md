### 数据集

`数据集（dataset）`是专门用来管理数据的组件。虽然每个系列都可以在 series.data 中设置数据，但是从 ECharts4 支持数据集开始，更推荐使用数据集来管理数据。因为这样，数据可以被多个组件复用，也方便进行 “数据和其他配置” 分离的配置风格

#### 在系列中设置数据

- 优点: 适于对一些特殊的数据结构（如“树”、“图”、超大数据）进行一定的数据类型定制
- 缺点: 需要用户先处理数据，把数据分割设置到各个系列（和类目轴）中。此外，不利于多个系列共享一份数据，也不利于基于原始数据进行图表类型、系列的映射安排

```js
option = {
  xAxis: {
    type: "category",
    data: ["Matcha Latte", "Milk Tea", "Cheese Cocoa", "Walnut Brownie"],
  },
  yAxis: {},
  series: [
    {
      type: "bar",
      name: "2015",
      data: [89.3, 92.1, 94.4, 85.4],
    },
    {
      type: "bar",
      name: "2016",
      data: [95.8, 89.4, 91.2, 76.9],
    },
    {
      type: "bar",
      name: "2017",
      data: [97.7, 83.1, 92.5, 78.1],
    },
  ],
}
```

#### 在数据集中设置数据

- 能够贴近数据可视化常见思维方式：（I）提供数据，（II）指定数据到视觉的映射，从而形成图表
- 数据和其他配置可以被分离开来。数据常变，其他配置常不变。分开易于分别管理
- 数据可以被多个系列或者组件复用，对于大数据量的场景，不必为每个系列创建一份数据
- 支持更多的数据的常用格式，例如`二维数组、对象数组`等，一定程度上避免使用者为了数据格式而进行转换

```js
// 二维数组
option = {
  legend: {},
  tooltip: {},
  dataset: {
    // 提供一份数据。
    source: [
      ["product", "2015", "2016", "2017"],
      ["Matcha Latte", 43.3, 85.8, 93.7],
      ["Milk Tea", 83.1, 73.4, 55.1],
      ["Cheese Cocoa", 86.4, 65.2, 82.5],
      ["Walnut Brownie", 72.4, 53.9, 39.1],
    ],
  },
  // 声明一个 X 轴，类目轴（category）。默认情况下，类目轴对应到 dataset 第一列。
  xAxis: { type: "category" },
  // 声明一个 Y 轴，数值轴。
  yAxis: {},
  // 声明多个 bar 系列，默认情况下，每个系列会自动对应到 dataset 的每一列。
  series: [{ type: "bar" }, { type: "bar" }, { type: "bar" }],
}

// 对象数组 格式
option = {
  legend: {},
  tooltip: {},
  dataset: {
    // 用 dimensions 指定了维度的顺序。直角坐标系中，如果 X 轴 type 为 category，
    // 默认把第一个维度映射到 X 轴上，后面维度映射到 Y 轴上。
    // 如果不指定 dimensions，也可以通过指定 series.encode
    // 完成映射，参见后文。
    dimensions: ["product", "2015", "2016", "2017"],
    source: [
      { product: "Matcha Latte", 2015: 43.3, 2016: 85.8, 2017: 93.7 },
      { product: "Milk Tea", 2015: 83.1, 2016: 73.4, 2017: 55.1 },
      { product: "Cheese Cocoa", 2015: 86.4, 2016: 65.2, 2017: 82.5 },
      { product: "Walnut Brownie", 2015: 72.4, 2016: 53.9, 2017: 39.1 },
    ],
  },
  xAxis: { type: "category" },
  yAxis: {},
  series: [{ type: "bar" }, { type: "bar" }, { type: "bar" }],
}
```

#### 数据到图形的映射

- 数据可视化的一个常见思路是：（I）提供数据，（II）指定数据到视觉的映射, 简而言之，可以进行这些映射的设定
  - 指定 `数据集` 的列（column）还是行（row）映射为 系列（series）。这件事可以使用 series.seriesLayoutBy 属性来配置。默认是按照列（column）来映射。
  - 指定维度映射的规则：如何从 dataset 的维度（一个“维度”的意思是一行/列）映射到坐标轴（如 X、Y 轴）、提示框（tooltip）、标签（label）、图形元素大小颜色等（visualMap）。这件事可以使用 series.encode 属性，以及 visualMap 组件来配置（如果有需要映射颜色大小等视觉维度的话）。上面的例子中，没有给出这种映射配置，那么 ECharts 就按最常见的理解进行默认映射：X 坐标轴声明为类目轴，默认情况下会自动对应到 dataset.source 中的第一列；三个柱图系列，一一对应到 dataset.source 中后面每一列

#### 把数据集(dataset)的行或列映射为系列(series)

用户可以使用 seriesLayoutBy 配置项，改变图表对于行列的理解。seriesLayoutBy 可取值:

- row: 表示数据集的每一行都映射为一个系列。
- column: 表示数据集的每一列都映射为一个系列。

```js
option = {
  legend: {},
  tooltip: {},
  dataset: {
    source: [
      ["product", "2012", "2013", "2014", "2015"],
      ["Matcha Latte", 41.1, 30.4, 65.1, 53.3],
      ["Milk Tea", 86.5, 92.1, 85.7, 83.1],
      ["Cheese Cocoa", 24.1, 67.2, 79.5, 86.4],
    ],
  },
  xAxis: [
    { type: "category", gridIndex: 0 },
    { type: "category", gridIndex: 1 },
  ],
  yAxis: [{ gridIndex: 0 }, { gridIndex: 1 }],
  grid: [{ bottom: "55%" }, { top: "55%" }],
  series: [
    // 这几个系列会出现在第一个直角坐标系中，每个系列对应到 dataset 的每一行。
    { type: "bar", seriesLayoutBy: "row", xAxisIndex: 0, yAxisIndex: 0 },
    { type: "bar", seriesLayoutBy: "row", xAxisIndex: 0, yAxisIndex: 0 },
    { type: "bar", seriesLayoutBy: "row", xAxisIndex: 0, yAxisIndex: 0 },
    // 这几个系列会出现在第二个直角坐标系中，每个系列对应到 dataset 的每一列。
    { type: "bar", seriesLayoutBy: "column", xAxisIndex: 1, yAxisIndex: 1 },
    { type: "bar", seriesLayoutBy: "column", xAxisIndex: 1, yAxisIndex: 1 },
    { type: "bar", seriesLayoutBy: "column", xAxisIndex: 1, yAxisIndex: 1 },
    { type: "bar", seriesLayoutBy: "column", xAxisIndex: 1, yAxisIndex: 1 },
  ],
}
```

#### 维度(dimension)

常用图表所描述的数据大部分是“二维表”结构，上述的例子中，我们都使用二维数组来容纳二维表

- 当我们把系列（series）对应到“列”的时候，那么每一列就称为一个“维度（dimension）”，而每一行称为数据项（item）。
- 反之，如果我们把系列（series）对应到表行，那么每一行就是“维度（dimension）”，每一列就是数据项（item）

维度可以有单独的名字，便于在图表中显示。维度名（dimension name）可以在定义在 dataset 的`第一行（或者第一列）`。

如下面的例子中，'score'、'amount'、'product' 就是维度名

从第二行开始，才是正式的数据

dataset.source 中第一行（列）到底包含不包含维度名，ECharts 默认会自动探测。

当然也可以设置 dataset.sourceHeader: true 显示声明第一行（列）就是维度，或者 dataset.sourceHeader: false 表明第一行（列）开始就直接是数据

维度的定义，也可以使用单独的 `dataset.dimensions` 或者 `series.dimensions` 来定义，这样可以同时指定维度名，和维度的类型（dimension type）：

```js
var option1 = {
  dataset: {
    dimensions: [
      { name: "score" },
      // 可以简写为 string ，表示 dimension name 。
      "amount",
      // 可以在 type 中指定维度类型。
      { name: "product", type: "ordinal" },
    ],
    source: [
      //...
    ],
  },
  // ...
}

var option2 = {
  dataset: {
    source: [
      // ...
    ],
  },
  series: {
    type: "line",
    // series.dimensions 会更优先于 dataset.dimension 采纳。
    dimensions: [
      null, // 可以设置为 null 表示不想设置维度名
      "amount",
      { name: "product", type: "ordinal" },
    ],
  },
  // ...
}
```

大多数情况下，我们并不需要去设置维度类型，因为 ECharts 会自动尝试判断。但是如果不足够准确时，可以手动设置维度类型

维度类型（dimension type）可以取这些值:

- 'number': 默认, 表示普通数据
- 'ordinal': 对于类目、文本这些 string 类型的数据，如果需要能在数轴上使用，须是 'ordinal' 类型。ECharts 默认会试图自动判断这个类型。但是自动判断也可能不准确，所以使用者也可以手动强制指定
- 'time': 表示时间数据。设置成 'time' 则能支持自动解析数据成时间戳（timestamp），比如该维度的数据是 '2017-05-10'，会自动被解析。如果这个维度被用在时间数轴（axis.type 为 'time'）上，那么会被自动设置为 'time' 类型
- 'float': 如果设置成 'float'，在存储时候会使用 TypedArray，对性能优化有好处
- 'int': 如果设置成 'int'，在存储时候会使用 TypedArray，对性能优化有好处

#### 数据到图形的映射（series.encode）

了解了维度的概念后，我们就可以使用 `series.encode` 来做映射。总体是这样的感觉

```js
var option = {
  dataset: {
    source: [
      ["score", "amount", "product"],
      [89.3, 58212, "Matcha Latte"],
      [57.1, 78254, "Milk Tea"],
      [74.4, 41032, "Cheese Cocoa"],
      [50.1, 12755, "Cheese Brownie"],
      [89.7, 20145, "Matcha Cocoa"],
      [68.1, 79146, "Tea"],
      [19.6, 91852, "Orange Juice"],
      [10.6, 101852, "Lemon Juice"],
      [32.7, 20112, "Walnut Brownie"],
    ],
  },
  xAxis: {},
  yAxis: { type: "category" },
  series: [
    {
      type: "bar",
      encode: {
        // 将 "amount" 列映射到 X 轴。
        x: "amount",
        // 将 "product" 列映射到 Y 轴。
        y: "product",
      },
    },
  ],
}
```

series.encode 声明的基本结构如下

- 其中冒号左边是坐标系、标签等特定名称，如 'x', 'y', 'tooltip' 等
- 冒号右边是数据中的维度名（string 格式）或者维度的序号（number 格式，从 0 开始计数），可以指定一个或多个维度（使用数组）

```js
// 在任何坐标系和系列中，都支持：
encode: {
  // 使用 “名为 product 的维度” 和 “名为 score 的维度” 的值在 tooltip 中显示
  tooltip: ['product', 'score']
  // 使用 “维度 1” 和 “维度 3” 的维度名连起来作为系列名。（有时候名字比较长，这可以避免在 series.name 重复输入这些名字）
  seriesName: [1, 3],
  // 表示使用 “维度2” 中的值作为 id。这在使用 setOption 动态更新数据时有用处，可以使新老数据用 id 对应起来，从而能够产生合适的数据更新动画。
  itemId: 2,
  // 指定数据项的名称使用 “维度3” 在饼图等图表中有用，可以使这个名字显示在图例（legend）中。
  itemName: 3
}

// 直角坐标系（grid/cartesian）特有的属性：
encode: {
  // 把 “维度1”、“维度5”、“名为 score 的维度” 映射到 X 轴：
  x: [1, 5, 'score'],
  // 把“维度0”映射到 Y 轴。
  y: 0
}

// 单轴（singleAxis）特有的属性：
encode: {
  single: 3
}

// 极坐标系（polar）特有的属性：
encode: {
  radius: 3,
  angle: 2
}

// 地理坐标系（geo）特有的属性：
encode: {
  lng: 3,
  lat: 2
}

// 对于一些没有坐标系的图表，例如饼图、漏斗图等，可以是：
encode: {
  value: 3
}
```

#### 默认的 series.encode

当 series.encode 并没有指定时，ECharts 针对最常见直角坐标系中的图表（折线图、柱状图、散点图、K 线图等）、饼图、漏斗图，会采用一些默认的映射规则。默认的映射规则比较简单，大体是

- 在坐标系中（如直角坐标系、极坐标系等）
  - 如果有类目轴（axis.type 为 'category'），则将第一列（行）映射到这个轴上，后续每一列（行）对应一个系列
  - 如果没有类目轴，假如坐标系有两个轴（例如直角坐标系的 X Y 轴），则每两列对应一个系列，这两列分别映射到这两个轴上
- 如果没有坐标系（如饼图）
  - 取第一列（行）为名字，第二列（行）为数值（如果只有一列，则取第一列为数值）。

#### 数据的各种格式

除了二维数组以外，dataset 也支持例如下面 key-value 方式的数据格式，这类格式也非常常见。但是这类格式中，目前并不支持 seriesLayoutBy 参数。

```js
dataset: [
  {
    // 按行的 key-value 形式（对象数组），这是个比较常见的格式。
    source: [
      { product: "Matcha Latte", count: 823, score: 95.8 },
      { product: "Milk Tea", count: 235, score: 81.4 },
      { product: "Cheese Cocoa", count: 1042, score: 91.2 },
      { product: "Walnut Brownie", count: 988, score: 76.9 },
    ],
  },
  {
    // 按列的 key-value 形式。
    source: {
      product: ["Matcha Latte", "Milk Tea", "Cheese Cocoa", "Walnut Brownie"],
      count: [823, 235, 1042, 988],
      score: [95.8, 81.4, 91.2, 76.9],
    },
  },
]
```

#### 多个 dataset 以及如何引用他们

```js
var option = {
  dataset: [
    {
      // 序号为 0 的 dataset。
      source: [],
    },
    {
      // 序号为 1 的 dataset。
      source: [],
    },
    {
      // 序号为 2 的 dataset。
      source: [],
    },
  ],
  series: [
    {
      // 使用序号为 2 的 dataset。
      datasetIndex: 2,
    },
    {
      // 使用序号为 1 的 dataset。
      datasetIndex: 1,
    },
  ],
}
```