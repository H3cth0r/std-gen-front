<script>
  import { PromptBox } from "$lib/components";
  import { MainTitle } from "$lib/components";
  import { PlanCard } from '$lib/components';

  const plans = [
    {
      title: 'Basic',
      features: ['Feature 1', 'Feature 2', 'Feature 3'],
      price: '$9.99/mo',
      isPopular: false
    },
    {
      title: 'Pro',
      features: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'],
      price: '$19.99/mo',
      isPopular: true
    },
    {
      title: 'Enterprise',
      features: ['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5', 'Feature 6'],
      price: '$29.99/mo',
      isPopular: false
    }
  ];
</script>

<div class="min-h-screen flex flex-col justify-center items-center p-4 sm:p-6 md:p-8">
  <div class="w-full max-w-7xl flex flex-col justify-evenly items-center space-y-8">
    <div class="w-full sm:w-4/5 md:w-3/4 lg:w-2/3 xl:w-1/2">
      <MainTitle />
    </div>
    <div class="w-full sm:w-4/5 md:w-3/4 lg:w-2/3 xl:w-1/2 h-48 sm:h-56 md:h-64">
      <PromptBox
        minHeight="50%"
        maxHeight="80%"
      />
    </div>
  </div>
</div>

<div class="card min-h-screen flex flex-col justify-center items-center bg-white p-4 sm:p-6 md:p-8">
  <h2 class="h2 mb-8 text-center">Choose Your Subscription Plan</h2>
  <div class="flex flex-wrap justify-center gap-8">
    {#each plans as plan}
      <PlanCard
        title={plan.title}
        features={plan.features}
        price={plan.price}
        isPopular={plan.isPopular}
      />
    {/each}
  </div>
</div>
