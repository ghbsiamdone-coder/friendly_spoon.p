from temporalio import activity, workflow

from datetime import timedelta

@activity.defn

async def friendly_message(name: str) -> str:

    return f"Hello, {name}! Welcome to Friendly Spoon."

@workflow.defn

class FriendlySpoonWorkflow:

    @workflow.run

    async def run(self, name: str) -> str:

        return await workflow.execute_activity(

            friendly_message,

            name,

            start_to_close_timeout=
