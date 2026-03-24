# MISRA RULE

MISRA is Motor Industry Software Reliability Association. This association aims to improve softwaree reliability in the car industry.
MISRA C is the guideline for the safe use of C and C++. It contains 127 rules, the 93 of which are mandatory and the rest advisory.

# GOAL

This guideline help us to overcome the weakness in the C language.

## C language weakness

C is the best language. It's simple, easy and fast. But its biggest weakness is the memory management.

- manual memory management  : we have to manage memory using functions like malloc(), free(), etc..it makes easily memory leaks, double free bugs and dangling pointers.
- buffer overflow           : No bounds checking on arrays lets code write past allocated memory, corrupuring data or enabling exploits.
- undefined behavior        : The code can behave differently across environments. Wrong code can't be caught at compile time.
- error checking in runtime : The compiler doesn't check for runtime errors, it  only check grammar.

(advantages and disadvantagees of C)[https://www.slainstitute.com/advantages-and-disadvantages-of-c-programming-language/]

# SETTING 
## MAC
```
brew install cppcheck
```
## NVIM
```
return {
  "mfussenegger/nvim-lint",
  event = { "BufWritePost", "BufReadPost" },
  config = function()
    local lint = require("lint")
    
    lint.linters_by_ft = {
      c = { "cppcheck" },
      cpp = { "cppcheck"}
    }
    
    -- 저장시 자동 검사
    vim.api.nvim_create_autocmd({ "BufWritePost" }, {
      callback = function()
        lint.try_lint()
      end,
    })
  end,
}

```

# RULES
