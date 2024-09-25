# Bootstrap OTEL Go client

This package aim to simplify and reduce line of code to integrate with OTEL lib.

## Usage
```go
...

import (
	"context"
	"github.com/5ylar/otelinit"
)

func main() {
	ctx := context.Background()
	shutdown := otelinit.Init(ctx)
	defer shutdown(ctx)

    ...

	ctx, span := otelinit.Tracer.Start(ctx, "test span name")
	defer span.End()

    ...

}
```

We can configure behavior of OTEL client via environment variables. For example:
```
OTEL_RESOURCE_ATTRIBUTES=service.name=example,example.name=basic
OTEL_EXPORTER_OTLP_ENDPOINT=http://localhost:4318
OTEL_TRACES_SAMPLER=parentbased_traceidratio
OTEL_TRACES_SAMPLER_ARG=1.0
OTEL_BSP_SCHEDULE_DELAY=2000
```
