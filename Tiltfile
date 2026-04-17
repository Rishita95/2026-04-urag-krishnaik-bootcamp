local_resource(
    name="litellm-prisma-generate",
    cmd="""
        echo "Generating Prisma schema for LiteLLM using uvx..."
        SCHEMA_PATH=$(uvx --from "litellm[proxy,extra-proxy]>=1.83.1" python -c "import litellm_proxy_extras; import os; print(os.path.join(os.path.dirname(litellm_proxy_extras.__file__), 'schema.prisma'))")
        uvx --from "litellm[proxy,extra-proxy]>=1.83.1" prisma generate --schema "$SCHEMA_PATH" > /dev/null
        echo "✓ Setup complete"
    """
)
