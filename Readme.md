This repository demonstrates multiple types of chains that can be created using LangChain (latest version).


1. Simple Chaining (llmChains.ipynb)
    In simple chaining, we can just bind the input variable to the default prompt and invoke the chain

    Steps : 
    A. Define LLM
    B. Define Prompt Template
    C. Define LLMChain 
    D. Invoke Chain(run method) with input variable(pass single)

2. Multiple Chains (multipleLLmM_chains.ipynb)
    While simple chaining works for basic prompts, real-world scenarios often require multiple input variables. Multiple chaining involves binding multiple variables to a single prompt, making it more flexible and dynamic.

    Steps:
    A. Define LLM
    B. Define Prompt Template (which accepts multiple variables)
    C. Define LLMChain 
    D. Invoke Chain(run method) with input variables that are required for prompt to run using dictionary.

3. Sequential Chains (Sequential_chains.ipynb)
    Sequential chaining extends multiple chains by linking multiple chains together, where the output of one chain becomes the input to the next (referenced as "output_key"). This is useful when chain execution depends on outputs from previous chains. 

    We use the RunnableSequence library from LangChain for this.

    Steps:
    A. Define LLM
    B. Define the initial prompt and associated chains, specifying the output_key that will be used by subsequent chains.
    C. Define additional prompts and their associated chains, providing inputs from previous chains' output_keys as needed.
    D. Define RunnableSequence with all chains separated by the "|" operator in sequence.
    E. Invoke the sequence using the sequence.invoke() method with required inputs.

4. Router Chains (router_chains.ipynb)
    In the previous three chain types, you explicitly define the execution flow. With router chains, you allow the LLM to dynamically decide which chain to execute based on user input, routing to the appropriate chain automatically.

    We use RunnableSequence and RunnableBranch for this.

    Steps:
    A. Define LLM
    B. Define the prompt templates for different types/use cases
    C. Define the RunnableBranch with lambda X value to be the type and associated chain with it.
    D. Invoke the branch with inputs required
