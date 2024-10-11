import openai
openai.api_key = "your_sk"

# prompt (assuming md_resume and job_desciption have been defined)
prompt = f"""
I have a resume formatted in Markdown and a job description. \
Please adapt my resume to better align with the job requirements while \
maintaining a professional tone. Tailor my skills, experiences, and \
achievements to highlight the most relevant points for the position. \
Ensure that my resume still reflects my unique qualifications and strengths \
but emphasizes the skills and experiences that match the job description.

### Here is my resume in Markdown:
{md_resume}

### Here is the job description:
{job_desciption}

Please modify the resume to:
- Use keywords and phrases from the job description.
- Adjust the bullet points under each role to emphasize relevant skills and achievements.
- Make sure my experiences are presented in a way that matches the required qualifications.
- Maintain clarity, conciseness, and professionalism throughout.

Return the updated resume in Markdown format.

"""
    
# make api call
response = openai.chat.completions.create(
    model="gpt-4o-mini",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": prompt}
    ], 
    temperature = 0.25
)
    
# extract response
resume = response.choices[0].message.content
