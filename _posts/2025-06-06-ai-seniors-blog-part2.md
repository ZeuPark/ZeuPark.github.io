---
title: "Building an AI Platform for Seniors: Facing Real-World Challenges"  
date: 2025-06-06  
layout: single  
tags:  
  - project  

excerpt: "When I started building my AI platform for seniors, I quickly discovered that good intentions weren't enough - I faced serious challenges in design, technology, and understanding user needs."  
---

## Why I studied this  

After setting my ambitious goals for an AI platform for seniors, it was time to actually build it. I thought the hard part was coming up with the idea, but I quickly learned that execution brings a whole new set of challenges. Every decision - from button colors to AI model selection - became more complex when designing for users with different needs and technical comfort levels.  

---

## What I did  

### Challenge 1: Designing for Low Digital Literacy  

I had to completely rethink how I approach interface design.  

#### Problems I Encountered  
- What font size is actually readable for older eyes?  
- Which colors provide enough contrast without being harsh?  
- How do I write instructions that don't sound condescending?  
- Should I use icons, text, or both for buttons?  

#### My Approach  
```html
<!-- Instead of small, technical buttons -->
<button class="btn-small">Process</button>

<!-- I designed large, clear buttons -->
<button class="btn-large">
  <span class="btn-icon">📝</span>
  <span class="btn-text">Help me write</span>
</button>
```

I focused on making everything bigger, clearer, and more descriptive.  

### Challenge 2: Choosing the Right AI Features  

This was harder than I expected - I kept second-guessing what seniors actually need.  

#### Features I Considered  
- Text summarization for news articles  
- Voice-to-text for easier typing  
- Photo description for accessibility  
- Scam detection for online safety  
- Simple image editing  

#### My Struggle  
I realized I was choosing features based on what I thought was cool, not what was actually useful. I had no real data about senior technology needs and couldn't find good research online.  

#### My Solution  
```python
# I started with the most basic AI feature  
def simple_text_helper(user_input):  
    # Help users write clearer messages  
    prompt = f"Make this message clearer and more polite: {user_input}"  
    response = ai_model.generate(prompt)  
    return response  

# Simple and practical  
```

### Challenge 3: Technical Integration Challenges  

Getting AI to work smoothly in a web application proved difficult.  

#### Problems I Faced  
- How do I connect FastAPI backend with React frontend?  
- Should I use cloud AI APIs or run models locally?  
- What happens if the AI is slow or fails?  
- How do I handle errors without confusing users?  

#### My Learning Process  
```python
# Simple FastAPI setup for AI endpoints  
from fastapi import FastAPI  
from fastapi.middleware.cors import CORSMiddleware  

app = FastAPI()  

# Enable CORS for frontend connection  
app.add_middleware(  
    CORSMiddleware,  
    allow_origins=["*"],  
    allow_methods=["*"],  
    allow_headers=["*"],  
)  

@app.post("/help-write")  
async def help_write_text(text: str):  
    try:  
        # Call AI service  
        result = ai_service.improve_text(text)  
        return {"success": True, "result": result}  
    except Exception as e:  
        # Simple error handling  
        return {"success": False, "error": "Something went wrong. Please try again."}  
```

### Challenge 4: Performance and Computing Limitations  

I worried about running AI models in real-time, especially on older computers in welfare centers.  

#### My Concerns  
- What if the computers are slow or old?  
- Can I rely on internet connections in community centers?  
- How do I make AI responses fast enough?  
- Should I cache common requests?  

#### My Solution Strategy  
- Use cloud AI APIs instead of local models  
- Design for graceful degradation if connection is slow  
- Add loading states that are clear and reassuring  
- Keep AI tasks simple and focused  

### Challenge 5: User Testing Reality Check  

When I finally tested with actual seniors, I discovered gaps in my assumptions.  

#### What I Expected  
- They would appreciate the large buttons  
- Simple language would be enough  
- They would understand the AI concept  

#### What Actually Happened  
- They were confused about what AI even means  
- They needed more explanation about what each feature does  
- They were worried about privacy and data safety  
- They wanted examples before trying features themselves  

---

## What I learned  

Building this platform taught me several important lessons about designing for accessibility:  

- **Assumptions are dangerous**: I thought I understood senior needs, but real user testing revealed I was wrong about many things  
- **Simple is incredibly hard**: Creating truly simple interfaces requires removing features, not adding them  
- **Performance matters more for some users**: Slow responses frustrated seniors more than younger users  
- **Trust is everything**: Seniors need to understand and trust the technology before they'll use it  
- **Context matters**: Features that work in a personal setting might not work in a community center  

The biggest realization was that technical challenges were actually easier to solve than human-centered design challenges. Getting the AI to work was straightforward compared to making it trustworthy and accessible.  

---

## What I want to do next  

- Conduct more user testing sessions with actual seniors  
- Simplify the interface even further based on feedback  
- Add better explanations about what AI is and how it helps  
- Implement privacy features that seniors can understand  
- Create tutorial videos showing real people using the platform  
- Test the platform in actual community center settings  

---