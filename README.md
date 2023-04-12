# Likvido.EfCore.SqlServerContextFactory [![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/Likvido/Likvido.EfCore.SqlServerContextFactory/nuget.yml)](https://github.com/Likvido/Likvido.EfCore.SqlServerContextFactory/actions/workflows/nuget.yml) [![Nuget](https://img.shields.io/nuget/v/Likvido.EfCore.SqlServerContextFactory)](https://www.nuget.org/packages/Likvido.EfCore.SqlServerContextFactory/)
Makes `IDesignTimeDbContextFactory` implementation simpler.
# Usage
```
public class AppDbContextFactory : IDesignTimeDbContextFactory<AppDbContext>
{
    private readonly ContextFactory<AppDbContext> _contextFactory;

    public ApplicationDbContextFactory(ContextFactory<AppDbContext> contextFactory)
    {
        _contextFactory = contextFactory;
    }

    public ApplicationDbContextFactory()
    {
        _contextFactory = new ContextFactory<AppDbContext>("../ProjectWithAppSettings");
    }

    public ApplicationDbContext CreateDbContext(string[] args)
    {
        return _contextFactory.CreateDbContext("ProjectWithMigrations");
    }
}
