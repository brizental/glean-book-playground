# Boolean

Boolean metrics are used for reporting simple flags.

## Recording API

### `set`

Sets a boolean metric to a specific value.

{{#include ../../../assets/tab_header.md}}

<div data-lang="Kotlin" class="tab">

```Kotlin
import org.mozilla.yourApplication.GleanMetrics.Flags

Flags.a11yEnabled.set(System.isAccesibilityEnabled())
```

</div>

<div data-lang="Java" class="tab">

```Java
import org.mozilla.yourApplication.GleanMetrics.Flags;

Flags.INSTANCE.a11yEnabled.set(System.isAccessibilityEnabled());
```

</div>


<div data-lang="Swift" class="tab">

```Swift
@testable import Glean

Flags.a11yEnabled.set(self.isAccessibilityEnabled)
```

</div>

<div data-lang="Python" class="tab">

```Python
from glean import load_metrics
metrics = load_metrics("metrics.yaml")

metrics.flags.a11y_enabled.set(is_accessibility_enabled())
```

</div>

<div data-lang="Rust" class="tab">

```
use glean_metrics;

flags::a11y_enabled.set(system.is_accessibility_enabled());
```

</div>

<div data-lang="Javascript" class="tab">

```js
import { flags } from "./path/to/generated/files/flags.js";

flags.a11yEnabled.set(true);
```

</div>

<div data-lang="Firefox Desktop" class="tab">

**C++**

```cpp
#include "mozilla/glean/GleanMetrics.h"

mozilla::glean::flags::a11y_enabled.Set(false);
```

**Javascript**

```js
Glean.flags.a11yEnabled.set(false);
```

</div>

{{#include ../../../assets/tab_footer.md}}

## Testing API

### `testGetValue`

Gets the recorded value for a given boolean metric.

{{#include ../../../assets/tab_header.md}}

<div data-lang="Kotlin" class="tab">

```Kotlin
import org.mozilla.yourApplication.GleanMetrics.Flags

assertTrue(Flags.a11yEnabled.testGetValue())
```

</div>

<div data-lang="Java" class="tab">

```Java
import org.mozilla.yourApplication.GleanMetrics.Flags;

assertTrue(Flags.INSTANCE.a11yEnabled.testGetValue());
```

</div>


<div data-lang="Swift" class="tab">

```Swift
@testable import Glean

XCTAssertTrue(try Flags.a11yEnabled.testGetValue())
```

</div>

<div data-lang="Python" class="tab">

```Python
from glean import load_metrics
metrics = load_metrics("metrics.yaml")

assert True is metrics.flags.a11y_enabled.test_get_value()
```

</div>

<div data-lang="Rust" class="tab">

```
use glean_metrics;

assert!(flags::a11y_enabled.test_get_value(None).unwrap());
```

</div>

<div data-lang="Javascript" class="tab">

```js
import { flags } from "./path/to/generated/files/flags.js";

assert(await flags.a11yEnabled.testGetValue());
```

</div>

<div data-lang="Firefox Desktop" class="tab">

**C++**

```cpp
#include "mozilla/glean/GleanMetrics.h"

ASSERT_EQ(false, mozilla::glean::flags::a11y_enabled.TestGetValue().value());
```

**Javascript**

```js
Assert.equal(false, Glean.flags.a11yEnabled.testGetValue());
```

</div>

{{#include ../../../assets/tab_footer.md}}

### `testHasValue`

Whether or not **any** value was recorded for a given boolean metric.

{{#include ../../../assets/tab_header.md}}

<div data-lang="Kotlin" class="tab">

```Kotlin
import org.mozilla.yourApplication.GleanMetrics.Flags

assertTrue(Flags.a11yEnabled.testHasValue())
```

</div>

<div data-lang="Java" class="tab">

```Java
import org.mozilla.yourApplication.GleanMetrics.Flags;

assertTrue(Flags.INSTANCE.a11yEnabled.testHasValue());
```

</div>


<div data-lang="Swift" class="tab">

```Swift
@testable import Glean

XCTAssertTrue(try Flags.a11yEnabled.testHasValue())
```

</div>

<div data-lang="Python" class="tab">

```Python
from glean import load_metrics
metrics = load_metrics("metrics.yaml")

assert True is metrics.flags.a11y_enabled.test_has_value()
```

</div>

<div data-lang="Rust" class="tab disabled"></div>

<div data-lang="Javascript" class="tab disabled"></div>

<div data-lang="Firefox Desktop" class="tab disabled"></div>

{{#include ../../../assets/tab_footer.md}}

## Metric parameters

Example boolean metric definition:

```yaml
flags:
  a11y_enabled:
    type: boolean
    description: >
      Records whether a11y is enabled on the device.
    bugs:
      - https://bugzilla.mozilla.org/000000
    data_reviews:
      - https://bugzilla.mozilla.org/show_bug.cgi?id=000000#c3
    notification_emails:
      - me@mozilla.com
    expires: 2020-10-01
```

### Extra metric parameters

N/A



## Data questions
<!-- We can include a tooltip pointing people to docs on how to come up with data questions here -->

- Is accessibility enabled?

